```
    expsum_fit(x::Union{T,AbstractVector{T}}, y::AbstractVector{T}, n::Int; m::Int = 1, withconst::Bool = true, init::Union{Nothing,ExpSumFitInit} = nothing) where {T <: Real}
```

`n` 個の指数関数と定数の合計をフィットします。

$$
    y = k + p_1 e^{\lambda_1 t} + p_2 e^{\lambda_2 t} + \ldots + p_n e^{\lambda_n t}
$$

キーワード `withconst` が `false` に設定されている場合、定数はフィットされず、`k=0` に設定されます。

`m` ストリップを使用した数値積分を行い、デフォルトの `m=1` は線形補間を使用します。`m=2` 以上は均一な間隔を必要とし、通常はより良い精度をもたらします。

`init` を渡すことで、必要なメモリの大部分を事前に割り当てることができ、[`expsum_init`](@ref) で初期化できます。

定数 `k` とベクトル `p`, `λ`, `τ` を含む `ExpSumFit` 構造体を返します。ここで、`τ = -1/λ` です。

アルゴリズムは [Matlab code of Juan Gonzales Burgos](https://github.com/juangburgos/FitSumExponentials) からのものです。
