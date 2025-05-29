```
refine!(
	refiner::NoRefiner, index::AbstractChunkIndex, result::AbstractRAGResult;
	kwargs...)
```

Simple no-op function for `refine!`. It simply copies the `result.answer` and `result.conversations[:answer]` without any changes.
