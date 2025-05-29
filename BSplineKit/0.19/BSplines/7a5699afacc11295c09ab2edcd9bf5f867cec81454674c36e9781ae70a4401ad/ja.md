```
static_length(::Type{<:AbstractBSplineBasis}) -> Union{Int, Nothing}
static_length(::AbstractBSplineBasis) -> Union{Int, Nothing}
```

基底の長さが静的に知られている場合（すなわち、コンパイル時に）その長さを返します。そうでない場合は `nothing` を返します。

通常、静的に知られている長さを持つ基底は、基底のブレークポイントを記述するために `SVector`（StaticArraysパッケージから）を使用して構築されたものです。
