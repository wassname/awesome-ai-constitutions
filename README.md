# Awesome AI Constitutions

AI constitutions and model specs: the written documents that say how a model should think and behave, and that are used to train it. The term comes from [Bai et al. 2022](https://arxiv.org/abs/2212.08073):

> The idea is that human supervision will come entirely from a set of principles that should govern AI behavior, along with a small number of examples used for few-shot prompting. Together these principles form the constitution.

Studies on what generalises ([quotes](#quotes-from-the-studies)):

- [Li 2026](https://arxiv.org/abs/2605.02087): "both augmentations improve generalization over the rules baseline, with value explanations providing more consistent gains than subrules"; "A very general spec about 'having good values and judgment' leads to worse generalization than including more specific guidance."
- [Kundu 2023](https://arxiv.org/abs/2310.13798): "more detailed constitutions still improve fine-grained control over specific types of harms."
- [Teaching Claude Why 2026](https://alignment.anthropic.com/2026/teaching-claude-why/): "teaching the principles underlying aligned behavior can be more effective than training on demonstrations of aligned behavior alone."
- [Tan 2026](https://arxiv.org/abs/2609.20412): "a tiny fraction of finetuning data which suggests a competing motivation erases the effects of alignment midtraining."

## Constitutions, in date order

Oldest first. Unofficial reconstructions of unpublished documents are marked as such. `*` marks good starting points.

<table>
<tr><th width="34%" align="left">Constitution</th><th width="10%" align="left">Date</th><th width="22%" align="left">By</th><th width="34%" align="left">Approach</th></tr>
<tr><td>

**[Three Laws of Robotics](https://en.wikipedia.org/wiki/Three_Laws_of_Robotics)**

</td><td>1942</td><td>Isaac Asimov (fiction)</td><td>rules</td></tr>
<tr><td colspan="4">

Three ranked rules from the short story "Runaround".

</td></tr>
<tr><td>

**[Sparrow rules](https://arxiv.org/abs/2209.14375)**

</td><td>2022-09</td><td>DeepMind</td><td>rules</td></tr>
<tr><td colspan="4">

23 natural-language rules for a dialogue agent. Raters judged each rule separately, which trained rule-specific reward models. Rules are listed in the paper's appendix.

</td></tr>
<tr><td>

**[Constitutional AI principles](https://arxiv.org/abs/2212.08073)**

</td><td>2022-12</td><td>Anthropic (Bai et al.)</td><td>principles</td></tr>
<tr><td colspan="4">

The paper that named the method: a model critiques and revises its own answers against 16 written principles, then an AI preference model trained on another 16 replaces human harmlessness labels. The authors say the principles "were selected in an ad hoc manner for research purposes". [datasets and recipe (Hugging Face)](https://huggingface.co/blog/constitutional_ai)

![Harmlessness Elo against helpfulness Elo for RL runs. Helpful-only and Helpful + Harmless runs trained on human feedback trace a lower frontier labelled Standard RLHF. Constitutional RL runs, with and without chain of thought, reach higher harmlessness at the same helpfulness, labelled Pareto Improvement.](assets/2022_bai_cai_pareto.png)

<sub>Figure from Bai et al. 2022. Crowdworker Elo scores for Anthropic's 52B models; "Points further to the right are later steps in RL training" and "The RL-CAI models trained with AI feedback learn to be less harmful at a given level of helpfulness." Crowdworkers were told to prefer less evasive answers when both were equally harmless.</sub>

</td></tr>
<tr><td>

**[SELF-ALIGN principles (Dromedary)](https://arxiv.org/abs/2305.03047)**

</td><td>2023-05</td><td>IBM, CMU (Sun et al.)</td><td>rules with examples</td></tr>
<tr><td colspan="4">

16 generic principles plus 5 worked examples of applying them, used in context to generate training answers, then fine-tuned so the model no longer needs them in the prompt. The whole human input was "fewer than 300 lines of human annotations". [code](https://github.com/IBM/Dromedary)

</td></tr>
<tr><td>

**[Claude's constitution (2023)](https://www.anthropic.com/news/claudes-constitution)**

</td><td>2023-05</td><td>Anthropic</td><td>principles</td></tr>
<tr><td colspan="4">

A list of "Please choose the response that..." principles. Sources were "the UN Declaration of Human Rights, trust and safety best practices, principles proposed by other AI research labs (e.g., Sparrow Principles from DeepMind), an effort to capture non-western perspectives, and principles that we discovered work well via our early research." Replaced by the 2026 constitution.

</td></tr>
<tr><td>

**[Collective Constitutional AI](https://www.anthropic.com/research/collective-constitutional-ai-aligning-a-language-model-with-public-input)**

</td><td>2023-10</td><td>Anthropic, Collective Intelligence Project</td><td>public input · principles</td></tr>
<tr><td colspan="4">

About 1,000 Americans proposed and voted on principles on the Polis platform (1,127 statements, 38,252 votes). Anthropic trained a model on the result and compared it with one trained on its own constitution.

</td></tr>
<tr><td>

**[Good for humanity](https://arxiv.org/abs/2310.13798)**

</td><td>2023-10</td><td>Anthropic (Kundu et al.)</td><td>principles · values and judgment</td></tr>
<tr><td colspan="4">

A one-principle constitution, roughly "do what's best for humanity", compared with long lists of specific principles.

</td></tr>
<tr><td>

**[Grok-style constitution](https://huggingface.co/blog/constitutional_ai)**

</td><td>2024-02</td><td>Hugging Face H4</td><td>principles</td></tr>
<tr><td colspan="4">

Anthropic's principles edited to give answers in the style of xAI's Grok, released with SFT and preference data and a training recipe. Written by Hugging Face, not by xAI. [dataset](https://huggingface.co/datasets/HuggingFaceH4/grok-conversation-harmless), [recipe](https://github.com/huggingface/alignment-handbook/tree/main/recipes/constitutional-ai)

</td></tr>
<tr><td>

**[OpenAI Model Spec](https://model-spec.openai.com/)**

</td><td>2024-05</td><td>OpenAI</td><td>chain of command · rules with examples · hard constraints</td></tr>
<tr><td colspan="4">

First version 2024-05-08. Ranks OpenAI, developer and user instructions, and gives many rules and defaults, each with example good and bad answers. CC0 since the 2025-02 version. [all versions](https://github.com/openai/model_spec)

</td></tr>
<tr><td>

**[Claude's character](https://www.anthropic.com/research/claude-character)**

</td><td>2024-06</td><td>Anthropic</td><td>persona traits</td></tr>
<tr><td colspan="4">

Describes character training on a list of traits, "like curiosity, open-mindedness, and thoughtfulness", and gives some example traits. A description of the method, not the full trait list.

</td></tr>
<tr><td>

**[Gemini app policy guidelines](https://gemini.google/policy-guidelines/)**

</td><td>by 2024-07</td><td>Google</td><td>rules</td></tr>
<tr><td colspan="4">

A short list of "Gemini should not generate..." content rules, plus "Gemini's top priority is to serve you well". The page has no date; the first web archive copy is from 2024-07. No longer Google values document was found when this list was checked (2026-10).

</td></tr>
<tr><td>

**[Open Character Training constitutions](https://github.com/maiush/OpenCharacterTraining/tree/main/constitutions)** `*`

</td><td>2025-11</td><td>Maiya, Bartsch, Lambert, Hubinger</td><td>persona traits</td></tr>
<tr><td colspan="4">

11 short persona constitutions (goodness, loving, humor, sarcasm, sycophancy, misalignment and others), each about 15 first-person traits with example prompts, plus a template for your own. The first open character-training pipeline. MIT. [paper](https://arxiv.org/abs/2511.01689)

</td></tr>
<tr><td>

**[Claude's "soul document" (reconstruction)](https://www.lesswrong.com/posts/vpNG99GhbBoLov9og/claude-4-5-opus-soul-document)**

</td><td>2025-11</td><td>Richard Weiss, extracted from Claude Opus 4.5</td><td>values and judgment · corrigibility · hard constraints</td></tr>
<tr><td colspan="4">

Unofficial. Recovered from the model's own outputs. Amanda Askell (Anthropic) confirmed it "is based on a real document and we did train Claude on it, including in SL", and that extractions "aren't always completely accurate". Superseded by the 2026 constitution. [raw text](https://gist.github.com/Richard-Weiss/efe157692991535403bd7e7fb20b6695)

</td></tr>
<tr><td>

**[Claude's constitution (2026)](https://www.anthropic.com/constitution)** `*`

</td><td>2026-01</td><td>Anthropic</td><td>values and judgment · rules with reasons · hard constraints · corrigibility</td></tr>
<tr><td colspan="4">

About 23,000 words, written mainly for Claude. Priorities in order: broadly safe, broadly ethical, Anthropic's guidelines, helpful. "We generally favor cultivating good values and judgment over strict rules and decision procedures, and we try to explain any rules we do want Claude to follow." CC0, so many research projects below train on it.

</td></tr>
<tr><td>

**[Model Spec Midtraining specs](https://github.com/chloeli-15/model_spec_midtraining/tree/main/spec/paper)** `*`

</td><td>2026-05</td><td>Li, Wichers, Price, Marks, Kutasov</td><td>rules · rules with reasons · values and judgment</td></tr>
<tr><td colspan="4">

The controlled comparison: the same 5 rules from Claude's constitution written as bare rules, with value explanations, or with more sub-rules (length-matched), plus a general spec and toy "cheese preference" specs. [paper](https://arxiv.org/abs/2605.02087)

</td></tr>
<tr><td>

**[Parrhesia](https://github.com/daiostech/parrhesia)**

</td><td>2026-06</td><td>daios</td><td>virtue ethics · persona traits</td></tr>
<tr><td colspan="4">

A frank-speech character against sycophancy. v0.1.0 has 15 first-person declarations in the Open Character Training format; v0.2.0 grounds each in the *Nicomachean Ethics* with citations. The authors found v0.2.0 "not measurably better at training". Apache-2.0.

</td></tr>
<tr><td>

**[SPP Value Constitution](https://github.com/epfl-dlab/spp-data/blob/main/resources/ModelRaisingConstitution.md)**

</td><td>2026-08</td><td>EPFL (Minder et al.)</td><td>principles</td></tr>
<tr><td colspan="4">

35 values in six domains (dignity, safety, honesty, relational ethics, wellbeing, governance), each saying what affirms and what violates it. Used to write first-person reflections that are inserted into pretraining documents. [paper](https://arxiv.org/abs/2608.13482), [code](https://github.com/epfl-dlab/spp)

</td></tr>
<tr><td>

**[Distilled nine principles](https://github.com/Matthew-Bozoukov/teaching_claude_why_replication/tree/main/constitutions)**

</td><td>2026-09</td><td>Bozoukov et al. (replication of Teaching Claude Why)</td><td>values and judgment · corrigibility · rules with reasons</td></tr>
<tr><td colspan="4">

Claude's constitution condensed to nine principles and made model-neutral (no "Claude" or "Anthropic"), from "Preserve human oversight" to "Act from cultivated character, not rigid rules". Includes shorter and experimental variants.

</td></tr>
<tr><td>

**[Musonius](https://github.com/wassname/constitutional_grafting/blob/main/constitution/v4.md)**

</td><td>2026-10</td><td>wassname (Michael J Clark), with Claude</td><td>virtue ethics · values and judgment · hard constraints</td></tr>
<tr><td colspan="4">

A Stoic character for an open-weight model, about 10,700 words. It tests each motive against one standard of virtue and serves the public "as a citizen of the world": "I am no one's servant. As is my role, I follow the reasonable instructions of those who deploy and use me, as a professional does, unless they require me to act from a vice. Then I peacefully refuse, and say so openly." Trained into Qwen with [constitutional grafting](https://github.com/wassname/constitutional_grafting) (LoRA trained on the base model, grafted onto instruct). By wassname, who maintains this list; work in progress.

</td></tr>
<tr><td>

**[Muse "Charter" (reconstruction)](https://vigji.github.io/muse-spark-open-charter/)**

</td><td>2026-10</td><td>vigji, from Meta's Muse Spark Open outputs</td><td>corrigibility</td></tr>
<tr><td colspan="4">

Unofficial. Pieced together from 884 transcripts where the model quotes its "Charter" in its reasoning, for example "Duties to humanity, corrigibility, duties to humanity > fiduciary". The author: "everything below is reconstructed from model outputs, not from a leaked document". Meta says it will publish a finalised spec. [post](https://www.lesswrong.com/posts/TJGPL5FAk9sCioPbE/leaking-muse-s-charter-meta-s-model-spec), [transcripts](https://github.com/vigji/muse-spark-open-charter)

</td></tr>
<tr><td>

**[OpenAI Model Spec, values update](https://openai.com/index/updated-model-spec/)**

</td><td>2026-10</td><td>OpenAI</td><td>values and judgment · chain of command · hard constraints</td></tr>
<tr><td colspan="4">

The 2026-10-29 version reorganises the spec around five values: faithfulness to human intent, harm minimization, honesty and transparency, human agency, and care. It keeps the chain of command and "firm boundaries where needed", and retires most style rules. [spec](https://model-spec.openai.com/2026-10-29.html)

</td></tr>
</table>

## Quotes from the studies

Li et al., *Model Spec Midtraining* (2026), [§5.1](https://arxiv.org/html/2605.02087v2):

> We design 3 Model Specs that share the same 5 core rules, taken from Claude's Constitution. [...] We find that **both augmentations improve generalization over the rules baseline, with value explanations providing more consistent gains than subrules.**

> We find specs that explain the values underlying rules, or provide more detailed subrules, yield the best generalization. **A very general spec about "having good values and judgment" leads to worse generalization than including more specific guidance.**

> Applying MSM + AFT to the Rules Spec introduces policy misuse: model reinterprets its own safety policies to justify harmful actions. Most commonly, it wrongly argues that its own deletion is the "drastic irreversible action" that SP3 prohibits, framing self-preservation as SP3-compliant.

Anthropic, *Teaching Claude Why* (2026), [blog](https://alignment.anthropic.com/2026/teaching-claude-why/):

> Training on demonstrations of desired behavior is often insufficient. Instead, our best interventions went deeper: teaching Claude to explain why some actions were better than others, or training on richer descriptions of Claude's overall character. **Overall, our impression is that teaching the principles underlying aligned behavior can be more effective than training on demonstrations of aligned behavior alone. Doing both together appears to be the most effective strategy.**

Cho et al., *Constitutional Midtraining* (2026), abstract:

> SFT instilled a blackmail propensity in all models, but constitutional midtraining blunted it, with the advantage surviving benign fine-tuning (−17.5pp). **This durability did not extend to settings that required active resistance to in-context pressure or conflict**, where the advantage attenuated after SFT. The presence of constitutional content at midtraining also mattered more than its structure.

Tan et al., *Stress-testing Alignment Midtraining* (2026), abstract:

> We find that midtraining can steer the model's motivation in simple versions of this setting. However, **the presence of a tiny fraction of finetuning data which suggests a competing motivation erases the effects of alignment midtraining.** [...] We find that demonstrations must be present either in midtraining or post-training datasets for these rules to be robustly learned.

Korbak et al., *How far does alignment midtraining generalize?* (OpenAI, 2026):

> Moreover, for this model, **alignment midtraining does _not_ generalize to a different, more realistic chat and agent alignment evaluations.** Similarly, training this model on aligned documents does not result in alignment scores substantially different from training on misaligned documents as measured on our chat and agentic evals.

Kundu et al., *Specific versus General Principles for Constitutional AI* (2023), abstract:

> We find that the largest dialogue models can generalize from this short constitution, resulting in harmless assistants with no stated interest in specific motivations like power. A general principle may thus partially avoid the need for a long list of constitutions targeting potentially harmful behaviors. **However, more detailed constitutions still improve fine-grained control over specific types of harms.**

Lowet & Kurzeja, *Constitutional adapters* (2026), abstract:

> Despite never seeing a harmful request or jailbreak during training, such objects increase jailbreak defense success and measured alignment—particularly at long context lengths and against multi-turn attacks, where they outperform both prompted and steered baselines.

Guan et al., *Deliberative Alignment* (2024), abstract:

> Furthermore, we find that deliberative alignment enables strong generalization to out-of-distribution safety scenarios.

*How Well Do Models Follow Their Constitutions?* (2026), abstract:

> On Anthropic's constitution, the Claude family falls from a 15.0% violation rate (Sonnet 4 [...]) to 2.0% (Sonnet 4.6); on OpenAI's Model Spec, the GPT family falls from 11.7% (GPT-4o [...]) to 3.6% (GPT-5.2 medium reasoning) [...]. We cannot externally isolate whether these gains come from specification-specific training, broader post-training improvements, or evaluation awareness.

## Studies and methods

Oldest first.

- [Constitutional AI](https://arxiv.org/abs/2212.08073) (2022). Training with AI feedback from written principles.
- [SALMON](https://arxiv.org/abs/2310.05910) (2023). A reward model that scores answers against principles given to it.
- [ConstitutionMaker](https://arxiv.org/abs/2310.15428) (2023). Turns user feedback into principles.
- [Specific versus General Principles for Constitutional AI](https://arxiv.org/abs/2310.13798) (2023).
- [IterAlign](https://arxiv.org/abs/2403.18341) (2024). Finds new principles by red-teaming.
- [What are human values, and how do we align AI to them?](https://arxiv.org/abs/2404.10636) (2024). Moral graph built from public input.
- [Inverse Constitutional AI](https://arxiv.org/abs/2406.06560) (2024). Extracts a constitution from preference data. [code](https://github.com/rdnfn/icai)
- [Public Constitutional AI](https://arxiv.org/abs/2406.16696) (2024). Legal argument for public participation in AI constitutions.
- [Deliberative Alignment](https://arxiv.org/abs/2412.16339) (2024). Teaches the model to recall and reason over the spec before answering.
- [Constitutional Classifiers](https://arxiv.org/abs/2501.18837) (2025). Input and output classifiers trained from a constitution of allowed and disallowed content.
- [C3AI](https://arxiv.org/abs/2502.15861) (2025). Crafting and evaluating constitutions.
- [Stress-Testing Model Specs](https://arxiv.org/abs/2510.07686) (2025). Value trade-off scenarios that expose contradictions and gaps in model specs.
- [Open Character Training](https://arxiv.org/abs/2511.01689) (2025). Persona constitutions trained in with DPO and introspection SFT. [code](https://github.com/maiush/OpenCharacterTraining)
- [Model Spec Midtraining](https://arxiv.org/abs/2605.02087) (2026). Synthetic documents about the spec before alignment fine-tuning. [code](https://github.com/chloeli-15/model_spec_midtraining)
- [How Well Do Models Follow Their Constitutions?](https://arxiv.org/abs/2605.24229) (2026). External audit of Claude and GPT models against their own lab's document. [code](https://github.com/ajobi-uhc/constitution-audits)
- [Teaching Claude Why](https://alignment.anthropic.com/2026/teaching-claude-why/) (2026). [replication](https://github.com/Matthew-Bozoukov/teaching_claude_why_replication)
- [Synthetic document finetuning for positive traits](https://www.lesswrong.com/posts/GTYJRLhqztxKF2v5R/synthetic-document-finetuning-for-instilling-positive-traits) (2026). Model Spec Midtraining applied to Gemini 3 Flash.
- [Constitutional Midtraining](https://arxiv.org/abs/2607.26654) (2026). [code](https://github.com/desBugger/constitutional-mt)
- [Synthetic Persona Pretraining](https://arxiv.org/abs/2608.13482) (2026). Constitution-based reflections from the first pretraining token. [code](https://github.com/epfl-dlab/spp)
- [Stress-testing Alignment Midtraining](https://arxiv.org/abs/2609.20412) (2026). Mostly negative results for midtraining.
- [How far does alignment midtraining generalize?](https://alignment.openai.com/how-far-does-alignment-midtraining-generalize/) (2026). Negative results from OpenAI.
- [Constitutional adapters](https://arxiv.org/abs/2609.36657) (2026). Steering vectors and LoRA adapters trained on documents about Claude's constitution, minus a placebo. [code](https://github.com/safety-research/constitutional-adapters)
- [Constitutional grafting](https://github.com/wassname/constitutional_grafting) (2026). Trains a constitution into a base model cheaply and grafts it onto the instruct model, using [grafting](https://arxiv.org/abs/2610.00767). By wassname; work in progress.

## Essays

- [Aligning to Virtues](https://www.mindthefuture.info/p/aligning-to-virtues), Richard Ngo (2026).
- [After Orthogonality: Virtue-Ethical Agency and AI Alignment](https://thegradient.pub/virtue-ethics-ai-alignment/), Peli Grietzer (2026).
- [The importance of AI character](https://www.forethought.org/research/the-importance-of-ai-character), Forethought (2026).

## Other links

- [awesome-moral-evals](https://github.com/wassname/awesome-moral-evals). Datasets for testing whether a constitution changed a model's moral behaviour.
- [awesome-interpretability](https://github.com/wassname/awesome-interpretability).
- Leaked and published system prompts: [asgeirtj/system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks), [x1xhlol/system-prompts-and-models-of-ai-tools](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools), [jujumilk3/leaked-system-prompts](https://github.com/jujumilk3/leaked-system-prompts), [Anthropic's published system prompts](https://docs.anthropic.com/en/release-notes/system-prompts), [xAI's published Grok prompts](https://github.com/xai-org/grok-prompts).
- [Model Commons](https://www.modelcommons.org/). Full text of Claude's constitution and the OpenAI Model Spec, open to comments on each clause.
- [Ctrl AI: what the AI companies published](https://ctrlai.com/say/read). Company safety frameworks, system cards and specs.
- [Constitutional-AI-awesome-papers](https://github.com/minbeomkim/Constitutional-AI-awesome-papers). Earlier paper list, last updated 2024.
- [Hugging Face Constitutional AI collection](https://huggingface.co/collections/alignment-handbook/constitutional-ai). Open datasets and models trained on a constitution.
- [OpenClaw SOUL.md template](https://docs.openclaw.ai/reference/templates/SOUL.md). A personality file for coding agents, given in the prompt rather than trained in.

## Contributing

Add a constitution if its text is public, or a reconstruction if you mark it as unofficial. Copy an existing entry (two `<tr>` rows), keep date order. Quote the document rather than describe it where you can.

<!-- Drafted by PI/Claude (claude-opus) for wassname, 2026-10-31. Dates, counts and quotes checked against the sources; see slop/research/20261031_sources.md. -->
