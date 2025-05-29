###### gattino レイヤースタイリング

```julia
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, args ...) -> ::Nothing
```

`style!` は、データに基づいてレイヤーデータのスタイリングを行うためのバインディングを持っています。

```julia
# 開いているコンポーネントの `vec` の値に基づいて `stylep` の値をスタイルします。
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, vec::Vector{<:Number}, stylep::Pair{String, Int64} ...)
# 各後続のコンポーネントを `vec` の各後続の要素でスタイルします。
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, key::String, vec::Vector{String})
# 通常のスタイリング：
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, p::Pair{String, String} ...)
```

`Context` 上のレイヤー `name` でも `style!` を使用できることに注意してください。

  * 参照: `animate!(::AbstractContext, ::String, ::ToolipsSVG.KeyFrames)`, `set!`, `Context`, `layers`, `open_layer!`

```example

```
