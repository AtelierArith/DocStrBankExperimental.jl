```
Line2D{N, VN<:AbstractVector{N}} <: AbstractPolyhedron{N}
```

2Dの線を表す型で、形式は $a⋅x = b$ です（すなわち、`Hyperplane` の特別なケースです）。

### フィールド

  * `a` – 法線方向（ゼロでない）
  * `b` – 制約

### 例

線 $y = -x + 1$:

```jldoctest
julia> Line2D([1., 1.], 1.)
Line2D{Float64, Vector{Float64}}([1.0, 1.0], 1.0)
```

代替コンストラクタは、2つの2D点（`AbstractVector`）`p` と `q` を取り、`p` から `q` への標準的な線を作成します。詳細は下のアルゴリズムセクションを参照してください。

```jldoctest
julia> Line2D([1., 1.], [2., 2])
Line2D{Float64, Vector{Float64}}([-1.0, 1.0], 0.0)
```

### アルゴリズム

2つの点 $p = (x₁, y₁)$ と $q = (x₂, y₂)$ が与えられたとき、これらの点を通る線は

$$
ℓ:~~y - y₁ = \dfrac{(y₂ - y₁)}{(x₂ - x₁)} ⋅ (x-x₁).
$$

特別な場合 $x₂ = x₁$ は、$y$-軸に平行な線（垂直線）を定義します。
