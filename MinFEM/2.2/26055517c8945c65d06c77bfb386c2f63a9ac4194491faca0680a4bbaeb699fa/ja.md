```julia
twonorm(
    v::AbstractVector{Float64},
    M::AbstractMatrix{Float64}
) -> Any

```

質量行列に基づく離散$L^2$-ノルムの実装。基底行列の代わりに質量行列の直接組み立てが可能であるため、p=2のpnormの高速バージョン。それぞれの質量行列に応じて、領域または境界に使用できます。
