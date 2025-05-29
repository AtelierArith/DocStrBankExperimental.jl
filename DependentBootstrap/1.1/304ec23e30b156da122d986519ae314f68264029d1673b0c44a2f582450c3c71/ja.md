```
dbootinds(data::T ; bi::BootInput)::Vector{Vector{Int}}
dbootinds(data::T ; kwargs...)::Vector{Vector{Int}}
```

返される `Vector{Vector{Int}}` の各内部ベクターは、元のデータセットをインデックスする際に使用されるインデックスを提供し、単一の再サンプリングデータセットを提供します。

`BootInput` のキーワードコンストラクタを呼び出すキーワードメソッドも提供されています。利用可能なキーワードの詳細については、REPL で `?BootInput` を使用してください。

単一の `Vector{Int}` 再サンプリングインデックスを取得したい場合は、`dbootinds_one` を使用してください。
