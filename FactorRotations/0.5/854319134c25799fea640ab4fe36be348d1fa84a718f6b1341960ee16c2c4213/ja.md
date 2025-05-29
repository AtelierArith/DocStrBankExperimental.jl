```
Varimax()
```

*Varimax*回転基準。

## 詳細

*Varimax*は、負荷行列$Λ ∈ ℝ^{p × k}$の列分散を最大化する直交回転法です：

$$
Q(Λ) = -\frac{p}{4} ∑_{j=1}^{k} \mathrm{Var}_i(Λ_{i, j}).
$$

これは、パラメータ`gamma = 1`の[`Oblimin`](@ref)回転基準の特別なケースです。

## 例

### 基準の設定

```jldoctest
julia> Varimax()
Varimax()
```

### VarimaxとObliminの同等性のテスト

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2"
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];

julia> L_varimax = rotate(L, Varimax());

julia> L_oblimin = rotate(L, Oblimin(gamma = 1, orthogonal = true));

julia> loadings(L_varimax) ≈ loadings(L_oblimin)
true
```
