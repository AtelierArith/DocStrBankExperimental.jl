```
fdiff_interpolation_expansion_polynom(σ::T [, k=3 [, notation=bwd]]) where T<:Real
```

有限差分展開係数ベクトルは、インデックス位置 $n$ に対するオフセット $σ$ での表形式の解析関数 $f[n]$ の $k^{th}$-次（デフォルトは *3* 次）ラグランジュ多項式補間を定義します。これは、インデックスが増加する場合は正、減少する場合は負です。

**前方差分表記** (`notation = fwd`)

この場合、表形式の区間 $f[n:n+k]$ を考えます。補間された値 $f[n-σ]$ は、前方差分展開によって与えられます。

$$
f[n-σ] = \sum_{p=0}^k α_p(σ) Δ^p f[n] + ⋯,
$$

ここで、展開係数は次のように与えられます。

[`fdiff_interpolation_expansion_polynom(σ, k, fwd)`](@ref) $→ α(σ) ≡ [α_0(σ),⋯\ α_k(σ)]$. 

応用：この多項式は、`f[n:n+k]` が知られている場合に *外挿* によって `f[n-1]` を予測するのに役立ちます（$σ=1$ を使用）。より一般的には、（実数）位置 $n ≤ v ≤ n+k$ に *補間* し、*外挿* によって `f[n-σ]` を予測するのに役立ちます（$σ > 0$ を使用）または $v>n+k$（$σ < -k$ を使用）。

注：前方オフセットは $σ ≡ n-v$ と定義されます。

**後方差分表記** (`notation = bwd`)

この場合、表形式の区間 $f[n-k:n]$ を考えます。補間された値 $f[n+σ]$ は、後方差分展開によって与えられます。

$$
f[n+σ] = \sum_{p=0}^k β_p(σ) ∇^p f[n] + ⋯,
$$

ここで、展開係数は次のように与えられます。

[`fdiff_interpolation_expansion_polynom(σ, k, bwd)`](@ref) $→ β(σ) ≡ [β_0(σ),⋯\ β_k(σ)]$. 

応用：この多項式は、`f[n-k:n]` が知られている場合に *外挿* によって `f[n+1]` を予測するのに役立ちます（$σ=1$ を使用）。より一般的には、（実数）位置 $n-k ≤ v ≤ n$ に *補間* し、*外挿* によって `f[n+σ]` を予測するのに役立ちます（$σ > 0$ を使用）または $v>n+k$（$σ < -k$ を使用）。

注：後方オフセットは $σ ≡ -(n-v)$ と定義されます。

#### 例：

```
julia> σ = 1; # 外挿に対応するオフセット

julia> α = fdiff_interpolation_expansion_polynom(σ, k, fwd); println("α = $α")
α = [1, -1, 1, -1, 1, -1]

julia> Fk = fdiff_expansion_weights(α, fwd, reg); println("Fk = $(Fk)")
Fk = [6, -15, 20, -15, 6, -1]

julia> β = fdiff_interpolation_expansion_polynom(σ, k, bwd); println("β = $β")
β = [1, 1, 1, 1, 1, 1]

julia> revBk = fdiff_expansion_weights(β, bwd, rev); println("revBk = $(revBk)")
revBk = [-1, 6, -15, 20, -15, 6]
```
