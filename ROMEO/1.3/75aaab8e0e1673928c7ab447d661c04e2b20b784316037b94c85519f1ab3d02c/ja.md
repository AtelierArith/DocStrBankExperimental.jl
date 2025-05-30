```
unwrap_individual(wrapped::AbstractArray{T,4}; TEs, keyargs...) where T
```

エコーの個別アンラッピングを行い、時間的アンラッピングは行いません。それでも、マルチエコー情報を使用して品質マップを改善します。この関数は、フラグ `individual=true` を持つ `unwrap` と同じです。構文は `unwrap` と同じですが、`temporal_uncertain_unwrapping` および `template` オプションはサポートしていません：
