```
compute(ctx::Context, d::Thunk; options=nothing) -> Chunk
```

Thunkを計算します - DAGを作成し、ノードにランクを割り当ててタイブレークを行い、指定されたオプションでスケジューラを実行します。結果を参照するChunkを返します。
