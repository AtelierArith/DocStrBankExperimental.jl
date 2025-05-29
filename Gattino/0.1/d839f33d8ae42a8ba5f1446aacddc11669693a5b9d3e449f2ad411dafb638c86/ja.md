```julia
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, args ...; keyargs ...)
```

`set!` は `open_layer!` と組み合わせて、要素のプロパティを設定するために使用されます - 通常はデータに基づいています。

```julia
# すべてのコンポーネントのプロパティを静的に設定します：
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, prop::Symbol, value::Any)
# `vec` に基づいて値をスケーリングし、`vec` の最大値の `100` パーセントに相当する値には `max` を使用します。
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, prop::Symbol, vec::Vector{<:Number}; max::Int64 = 10)
# 値を設定します
set!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.Servable}, prop::Symbol, vec::Vector{<:AbstractString})
```

同じディスパッチは `style!` にも利用可能です。

  * 参照: `style!`, `set_gradient!`, `open_layer!`, `set_shape!`, `Context`

```example

```
