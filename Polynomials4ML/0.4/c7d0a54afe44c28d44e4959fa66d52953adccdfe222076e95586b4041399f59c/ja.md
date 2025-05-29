`function orthpolybasis(...)` : 指定された内積に関して一変数の直交多項式基底を構築します。標準の3項再帰多項式の場合は、`legendre_basis`、`jacobi_basis`、または`chebyshev_basis`を使用してください。

現在、`orthpolybasis`は以下のコンストラクタを持つ離散重みの直交多項式を実装しています：

```julia
orthpolybasis(N::Integer, W::DiscreteWeights{TW}; TX = Float64)
orthpolybasis(N::Integer, X::AbstractVector{<: Real}, 
              W::AbstractVector{<: Real}, normalizeW=false; kwargs...)
```
