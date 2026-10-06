# AI Video Generator — Project Plan

## Background

As AI becomes part of everyday work, our colleagues are relying on it more often. To help the company build secure, durable capabilities for the future, we are exploring foundational infrastructure that we can understand, operate, and adapt ourselves.

This project will turn a written script into a complete AI-assisted video with a single workflow. Existing open-source tools provide useful building blocks, but many produce only very short clips—often just a few dozen seconds. We want to support longer, coherent videos and a workflow that can grow with the company’s needs.

## Vision

Investigate the capabilities and user experience of InVideo AI (`invideo.io`) and build an independent, company-tailored video generation platform. The initial goal is to cover the major capabilities users expect from the product, then develop a distinctive style and workflows suited to our company.

This project will use publicly available product information, documented interfaces, and open-source implementations as references. It will be implemented independently: no copying of proprietary source code, private assets, or protected design materials, and no bypassing access controls. The goal is comparable utility, not a claim of affiliation or an exact reproduction.

## Goals

- Accept a script or prompt and generate a structured video project.
- Produce videos substantially longer than the short clips common in current open-source examples.
- Support scene planning, visual selection or generation, narration, captions, music, and timeline assembly.
- Let users review and revise the script, scenes, voice, visuals, and timing before export.
- Provide a modular foundation that can use replaceable AI models and media providers.
- Prioritize company security, privacy, maintainability, and control over data and infrastructure.
- Establish an initial feature set by studying public product behavior and testing open-source alternatives.

## Non-Goals

- Reproducing InVideo AI’s private implementation or obtaining its source code.
- Using unauthorized access, reverse engineering that violates applicable terms, or extracting private data.
- Matching every feature in the first release.
- Depending on one model, vendor, or media library where practical alternatives exist.

## Initial Feature Scope

### Script to video

- Script and prompt input, with language and target duration settings.
- Script outlining and division into scenes.
- Scene descriptions, suggested visuals, and editable narration.
- Draft video generation with progress and error reporting.

### Editing and assembly

- Scene-level replacement, reordering, trimming, and regeneration.
- Narration and caption editing, with timing controls.
- Background music and volume controls.
- Preview and export to common video formats and resolutions.

### Platform foundations

- Project and asset management.
- Provider abstraction for language, speech, image/video, and media search services.
- Queueing and resumable jobs for longer renders.
- Configuration for retention, access control, and deployment within company infrastructure.

## Suggested Architecture

1. **Project API and UI** — manage scripts, scenes, assets, edits, and exports.
2. **Planning service** — transform a prompt or script into a timed scene plan and narration draft.
3. **Media adapters** — connect approved generation models and licensed stock-media sources through replaceable interfaces.
4. **Render pipeline** — combine scenes, voice, captions, and audio using established media tooling such as FFmpeg.
5. **Job queue and storage** — handle long-running generation, retries, project assets, and output files.
6. **Policy and observability layer** — track provider usage, costs, failures, provenance, and retention settings.

The architecture should keep provider-specific code behind adapters so the project can change models or vendors without rewriting the workflow.

## Delivery Phases

### Phase 1: Research and requirements

- Document publicly observable InVideo AI workflows and expected user outcomes.
- Review relevant open-source video generation and editing projects.
- Compare licensing, output duration, quality, operational requirements, and provider constraints.
- Define a feature matrix, threat model, data policy, and measurable acceptance criteria.

### Phase 2: Working prototype

- Build script intake, scene planning, narration, and a basic render pipeline.
- Support a longer end-to-end video using configurable scene count and duration.
- Provide a simple review-and-edit loop before export.

### Phase 3: Feature parity by user workflow

- Add scene regeneration, media selection, caption timing, audio controls, and project persistence.
- Improve render reliability, resumability, and quality controls.
- Compare workflows against documented product capabilities and close the highest-value gaps.

### Phase 4: Company-specific product

- Add company templates, brand rules, approved assets, deployment options, and access policies.
- Evaluate quality and cost with representative internal use cases.
- Define operational ownership, maintenance, and a roadmap for additional capabilities.

## Success Criteria

- A user can turn a script into a reviewable, editable video through one coherent workflow.
- The system can produce videos longer than the short-clip baseline, subject to configured provider and compute limits.
- Users can revise scenes and regenerate selected parts without restarting the entire project.
- The pipeline reports progress, handles failures, and can resume long-running jobs.
- Provider usage, asset provenance, data retention, and export settings are documented and configurable.
- The initial release has clear setup instructions, licensing information, and reproducible deployment steps.

## Risks and Open Questions

- Video generation providers may impose duration, rate, cost, or commercial-use limits.
- Long videos require scene consistency, stable timing, and efficient rendering; these need evaluation early.
- Model and media licenses, privacy terms, and data residency must be reviewed before production use.
- “Feature parity” should be measured by user workflows and outcomes, since the closed product’s internal behavior is not available for inspection.
- The project needs decisions on target users, preferred deployment model, supported languages, and acceptable per-video cost.

## Contribution Principles

- Prefer independently designed implementations and clearly licensed dependencies.
- Record design decisions, provider limitations, and media provenance.
- Keep credentials out of source control and provide secure configuration examples.
- Make provider integrations replaceable and document required permissions and costs.
- Treat generated media and user scripts according to the project’s retention and privacy policy.

## First Milestones

1. Publish a feature comparison and requirements document.
2. Select the initial open-source media pipeline and approved AI providers.
3. Deliver a prototype that turns a script into a multi-scene narrated video.
4. Add editing, regeneration, and resumable rendering.
5. Validate the workflow with company-specific examples and publish a prioritized roadmap.
