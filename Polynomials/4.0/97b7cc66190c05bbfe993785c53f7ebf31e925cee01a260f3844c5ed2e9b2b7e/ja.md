```
ChebyshevT{T, X}(coeffs::AbstractVector)
```

チェビシェフ多項式の第一種。

与えられた変数 `var` に関して、最低次からの係数 `coeffs` から多項式を構築します。`var` は文字、シンボル、または文字列であることができます。

!!! note
    `ChebyshevT` は軸を意識しておらず、`coeffs` を単に係数のリストとして扱い、最初のインデックスは常に `T_0(x)` の係数に対応します。


# 例

```jldoctest ChebyshevT
julia> using Polynomials

julia> p = ChebyshevT([1, 0, 3, 4])
ChebyshevT(1⋅T_0(x) + 3⋅T_2(x) + 4⋅T_3(x))

julia> ChebyshevT([1, 2, 3, 0], :s)
ChebyshevT(1⋅T_0(s) + 2⋅T_1(s) + 3⋅T_2(s))

julia> one(ChebyshevT)
ChebyshevT(1.0⋅T_0(x))

julia> p(0.5)
-4.5

julia> Polynomials.evalpoly(5.0, p, false) # p(5.0) で行われるドメインチェックをバイパスします
2088.0
```

後者は、`ChebyshevT` 多項式をそのドメイン `[-1,1]` の外で評価する方法を示しています。（新しいバージョンの `Julia` では、`evalpoly` は Base からエクスポートされた関数であり、このパッケージでメソッドが拡張されているため、モジュールの修飾は不要です。）

!!! note
    チェビシェフ多項式は、`ApproxFun`、`ClassicalOrthogonalPolynomials.jl`、`FastTransforms.jl`、および `SpecialPolynomials.jl` にも実装されています。

