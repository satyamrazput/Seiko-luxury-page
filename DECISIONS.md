# DECISIONS.md

1. Ingestion Strategy & Rejected Alternatives
I opted for a periodic batch ingestion strategy** (via scheduled background jobs or standard REST payloads) over a real-time streaming alternative (such as WebSockets or Kafka). 
- The Why: Batch processing significantly reduces system complexity, database write-locks, and infrastructure overhead. 
- The Rejection: While real-time streaming is the obvious choice for instant data availability, it introduces unnecessary points of failure and scaling challenges for a baseline prototype. Minute-level data freshness was sufficient for these project requirements, making batch processing the most pragmatic and stable choice.

2. Time-Limit Trade-offs & Future Improvements
- The Trade-off: Under the strict time limit, I bypassed implementing a comprehensive automated retry mechanism and a dead-letter queue (DLQ) for failed ingestion payloads. Currently, network timeouts or malformed data rejections are simply caught and logged rather than safely queued for reprocessing.
- With a Real Week: I would engineer a resilient data pipeline featuring exponential backoff for transient errors. I would also implement a DLQ to isolate bad data without halting the main queue, and expand the test coverage (unit and integration) to ensure edge cases are handled gracefully.

3. AI Tool Usage & Manual Verification
- AI Utilization: I utilized AI assistance primarily for rapid scaffolding of boilerplate code, structuring complex CSS layouts, and drafting the initial Three.js geometric setup for the front-end rendering.
- Manual Verification & Changes: I did not deploy the AI output blindly. I manually adjusted the 3D mesh parameters, updated the texture mapping to accurately reflect specific image files, and completely refactored the audio logic to use native HTML5 video audio rather than synthetic sound generation. Additionally, I strictly audited the final codebase to strip out all generated comments and ensure clean, production-ready formatting.
