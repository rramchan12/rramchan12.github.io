---
layout: default
title: "CBSE Learning Agent"
description: "A prototype for curriculum-grounded, AI-assisted tutoring"
---

# CBSE Learning Agent

Students often need help when a teacher is not available. A generic chatbot can answer quickly, but it may ignore the syllabus or invent facts. This prototype tests a narrower approach: retrieve relevant CBSE material first, then generate the explanation.

[Open the prototype →](https://cbselearningagent.streamlit.app/){: .btn .btn-primary}

> The hosted application currently requires access through Streamlit. This is a prototype, not a production education service.
{: .evidence-note}

---

## What I built

The prototype combines four components:

1. **Streamlit interface** for questions and responses.
2. **Python and LangChain orchestration** for prompt and retrieval flow.
3. **Vector search** over curriculum material.
4. **An OpenAI language model** to generate a grounded response.

The design tests three tasks:

- Explain a curriculum concept in simpler terms.
- Answer a question using retrieved course material.
- Generate practice questions for a selected topic.

The narrow scope is intentional. It makes answer quality easier to inspect than an open-ended tutoring claim.

---

## Why retrieval comes first

The failure mode is clear: fluent answers can still be wrong. The system retrieves curriculum context before generation. The model receives that context with the student's question.

This mechanism does not eliminate hallucinations. It makes them easier to detect and measure.

A production version would need:

- Source citations in every answer.
- Syllabus and textbook version tracking.
- Evaluation sets by subject and grade.
- Teacher review for high-risk content.
- Privacy controls for student data.
- Cost and latency limits.

---

## Evaluation plan

A useful tutoring system must pass more than a demo. I would measure:

| Measure | Question |
| --- | --- |
| Groundedness | Does the answer follow the retrieved curriculum source? |
| Correctness | Is the explanation factually and mathematically correct? |
| Instruction quality | Does the response explain the method, not only the answer? |
| Difficulty fit | Does the answer match the student's grade and requested depth? |
| Citation quality | Can the student trace the answer to a source? |
| Safety | Does the system avoid harmful, private, or inappropriate output? |

No student-impact claim is published because the prototype has no verified study or outcome dataset.

---

## Technical decisions

**Use retrieval instead of model memory alone.** CBSE scope and source material should constrain the answer.

**Keep orchestration visible.** Each stage—retrieve, assemble context, generate, and return—should be inspectable.

**Separate shipped behavior from roadmap.** Progress tracking, adaptive difficulty, mock tests, regional languages, handwriting input, and multimodal lessons remain future work unless validated in the deployed application.

**Measure before scaling.** The next release should add a small, reviewed benchmark before adding more subjects or features.

---

## Next decisions

1. Select one grade and two subjects for the first benchmark.
2. Build a teacher-reviewed question and answer set.
3. Add source citations and answer-level feedback.
4. Measure correctness, groundedness, latency, and cost.
5. Decide whether the results justify a broader pilot.

---

## About the project

I built this prototype to test how retrieval and agent workflows can support education. The same operating principle applies to enterprise AI: constrain the task, expose the mechanism, measure the result, and keep a human decision point where errors matter.

Questions or feedback: [email](mailto:ravi.ramchandran01@gmail.com) · [LinkedIn](https://www.linkedin.com/in/raviramchandran/)
