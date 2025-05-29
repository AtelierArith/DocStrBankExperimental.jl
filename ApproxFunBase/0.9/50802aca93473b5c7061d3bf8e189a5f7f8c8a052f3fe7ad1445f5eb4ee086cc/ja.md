```
ProductFun(coeffs::AbstractMatrix{T}, sp::AbstractProductSpace; [tol=100eps(T)], [chopping=false]) where {T<:Number}

二変数関数 `f` を係数行列 `coeffs` を用いて表現します。係数は、基底 `sp` における関数 `f` の二変数変換を使用して取得されます。

# 例

```

jldoctest julia> P = ProductFun([0 0; 0 1], Chebyshev() ⊗ Chebyshev()) # (x,y) -> x*y に対応 ProductFun on Chebyshev() ⊗ Chebyshev()

julia> P(0.1, 0.2) ≈ 0.1 * 0.2 true

```

```
