```
printmodel(io::IO, m::AbstractModel; kwargs...)
displaymodel(m::AbstractModel; kwargs...)
```

モデル `m` の文字列表現を印刷または返します。

# 引数

  * `header::Bool = false`: `true` に設定すると、`m` の `info` 構造を表示するヘッダーが印刷されます;
  * `show_subtree_info::Bool = false`: `true` に設定すると、`m` のサブツリー内のモデルに対してヘッダーが印刷されます;
  * `show_metrics::Bool = false`: `true` に設定すると、サブツリーの各ポイントでパフォーマンスメトリクスが表示されます。これらは `info` 構造に利用可能な場合に限ります;
  * `max_depth::Union{Nothing,Int} = nothing`: `Int` の場合、`max_depth` より深いサブツリー内のモデルは "..." で省略されます;
  * `syntaxstring_kwargs::NamedTuple = (;)`: 論理式のフォーマットのために `syntaxstring` に渡される kwargs。

[`syntaxstring`](@ref) および [`AbstractModel`](@ref) も参照してください。
