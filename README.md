# CAMELEON
### Cognitively Adaptive Memory with Emotion-weighted Layered Expert Orchestration Network

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20726337.svg)](https://doi.org/10.5281/zenodo.20726337)

> An architecture concept for AI agents that grow more personalised through lived interaction — not retraining, not prompt engineering, not memory databases. Through the design itself.

---

## The Problem

Every LLM you talk to today resets. The model you finish a conversation with is identical to the one you started with. No matter how long you've used it, it remains equally generic with you as it does with everyone else.

Current "memory" solutions patch over this with external databases and context injection — but that's not memory. That's a sticky note. The model itself is unchanged.

CAMELEON proposes a different architecture entirely.

---

## What CAMELEON Is

CAMELEON is a cognitive architecture for persistent AI agents built around five core mechanisms:

**1. Interaction-Consolidation Loop**
Modelled on the human sleep-wake cycle. During interaction, exchanges are logged. During idle periods, a lightweight consolidation process reviews logs, scores relevance, reinforces high-weight memories, and prunes low-weight ones. The agent manages its own memory.

**2. Interpretable Domain-Expert Routing**
Rather than one general-purpose model, a collection of domain-specific expert models sit behind a lightweight keyword saliency router. The router is rule-based and fully transparent — you can see exactly why a prompt went where it did and correct it when wrong. This is a deliberate departure from standard MoE (Mixture of Experts) architectures where routers are black-box weight matrices.

**3. Speculative Context Pre-Activation**
Borrowed from CPU branch prediction. The router doesn't just respond to the current prompt — it analyses conversation trajectory and pre-warms the most likely next expert before the user asks. Wrong predictions are discarded cheaply. Right ones reduce latency significantly.

**4. Emotion-Weighted Context Compression**
Current context management treats all tokens as equally important. CAMELEON uses emotion scoring as the primary compression signal — high-salience exchanges are retained losslessly, low-salience content is compressed aggressively, and model uncertainty in emotion scoring produces the natural variance that prevents the system becoming rigid. The emotion detector isn't built from scratch — it taps implicit affective encoding already present in models trained on human text.

**5. Time-Decay Relevance Scoring**
Relevance is a function of recency, recall frequency, and emotion weight. Memories that aren't accessed decay. Memories that keep getting recalled stay sharp. No manual curation required.

---

## The Core Property

The longer you use it, the more it becomes *your* model rather than *a* model.

Day one — generic. Month one — anticipates your domain. Year one — has a genuine model of how you think.

Switching to a fresh instance represents actual loss, because the accumulated personalisation lives in the architecture's state, not in a database you can export.

---

## Relationship to Existing Research

These ideas were derived independently from first principles — drawing analogies from CPU scheduling, audio compression (lossless vs lossy), child cognitive development, and neuroscience — before being validated against literature. Post-derivation search confirmed:

- The expert routing architecture corresponds to Mixture of Experts (MoE), the basis of GPT-4, Mixtral, and DeepSeek-R1. The interpretable rule-based router variant is not standard in current implementations.
- Emotion-weighted memory consolidation is an active research area (Affective GWR, Self-Reflective Emotional RAG). Existing work operates at the retrieval layer. CAMELEON proposes weight-level consolidation — currently unexplored.
- Speculative context pre-activation has no direct equivalent in current literature.

This is not a claim of invention in isolation. It is a record of independent derivation that converges with active research, arrived at through reasoning rather than literature review.

---

## Hardware Constraints

The full architecture — particularly weight-level modification during consolidation — exceeds current consumer hardware. A practical implementation path:

- **Phase 1 (CPU-only):** Interaction-consolidation loop with SQLite memory store and context injection. Proves the architecture in principle.
- **Phase 2 (Cloud GPU):** LoRA adapter generation during consolidation. True weight modification, not injection.
- **Phase 3 (Post-silicon):** Full continuous weight modification. Requires neuromorphic-compatible hardware. The brain does all of this on ~20 watts. Silicon cannot, yet.

---

## Full Architecture Document

See [`CAMELEON_Architecture_v0.1.docx`](./CAMELEON_Architecture_v0.1.docx) for the complete concept document including detailed mechanism descriptions, neuroscience grounding, and research context.

---

## Citation

If you reference this work, please cite:

```
Rajkumar A. (2026). CAMELEON: Cognitively Adaptive Memory with 
Emotion-weighted Layered Expert Orchestration Network. 
Zenodo. https://doi.org/10.5281/zenodo.20726337
```

---

## Origin

This architecture emerged from a single conversation in June 2026, starting from a practical question about AI limitations and arriving at a coherent system through analogy and first-principles reasoning. The [Tensora project](https://github.com/rajkumart5897/Tensora) documents a prior exploration that identified the same root problem from a different angle — the absence of persistent reasoning across context boundaries. That failure is the origin story of this architecture.

The full derivation conversation is preserved in [`origin/derivation_conversation_june2026.txt`](./origin/derivation_conversation_june2026.txt) with its original timestamp.

---

*Rajkumar A — June 2026*
