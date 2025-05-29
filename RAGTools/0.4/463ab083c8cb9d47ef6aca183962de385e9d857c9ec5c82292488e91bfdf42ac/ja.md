```
refine!(
	refiner::NoRefiner, index::AbstractChunkIndex, result::AbstractRAGResult;
	kwargs...)
```

`refine!`のための単純なノーオプ関数です。`result.answer`と`result.conversations[:answer]`を変更せずに単純にコピーします。
