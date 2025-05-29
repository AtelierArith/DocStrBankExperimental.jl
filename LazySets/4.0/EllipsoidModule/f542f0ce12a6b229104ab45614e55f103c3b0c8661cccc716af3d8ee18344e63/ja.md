```
Ellipsoid{N<:AbstractFloat, VN<:AbstractVector{N},
          MN<:AbstractMatrix{N}} <: AbstractCentrallySymmetric{N}
```

楕円体を表す型です。

これは次の集合として定義されます。

$$
E = \left\{ x ∈ ℝ^n : (x-c)^T Q^{-1} (x-c) ≤ 1 \right\},
$$

ここで、$c ∈ ℝ^n$ はその *中心* であり、$Q ∈ ℝ^{n×n}$ はその *形状行列* で、正定値行列である必要があります。楕円体は、可逆線形変換によってユークリッド球の像としても特徴付けられます。これは楕円の高次元一般化です。

### フィールド

  * `center`       – 楕円体の中心
  * `shape_matrix` – 実正定値行列、すなわち、転置行列と等しく、すべての非ゼロの $x$ に対して $x^\mathrm{T}Qx > 0$ である

## 注意事項

デフォルトでは、内部コンストラクタは与えられた形状行列が正定値であることを確認します。このチェックを無効にするには、フラグ `check_posdef=false` を使用します。

### 例

中心が `[1, 1]` の二次元楕円体を作成します：

```jldoctest ellipsoid_constructor
julia> using LinearAlgebra

julia> E = Ellipsoid(ones(2), Diagonal([2.0, 0.5]))
Ellipsoid{Float64, Vector{Float64}, Diagonal{Float64, Vector{Float64}}}([1.0, 1.0], [2.0 0.0; 0.0 0.5])
```

中心が指定されていない場合、原点であると仮定されます。例えば、原点に中心を持ち、形状行列が単位行列である三次元楕円体は次のように作成できます：

```jldoctest ellipsoid_constructor
julia> E = Ellipsoid(Matrix(1.0I, 3, 3))
Ellipsoid{Float64, Vector{Float64}, Matrix{Float64}}([0.0, 0.0, 0.0], [1.0 0.0 0.0; 0.0 1.0 0.0; 0.0 0.0 1.0])

julia> dim(E)
3
```

楕円体の中心と形状行列は、それぞれ `center` と `shape_matrix` 関数を使用して取得できます：

```jldoctest ellipsoid_constructor
julia> center(E)
3-element Vector{Float64}:
 0.0
 0.0
 0.0

julia> shape_matrix(E)
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```

関数 `an_element` は楕円体のいくつかの要素を返します：

```jldoctest ellipsoid_constructor
julia> an_element(E)
3-element Vector{Float64}:
 0.0
 0.0
 0.0

julia> an_element(E) ∈ E
true
```

与えられた方向、例えば `[1, 1, 1]` におけるサポートベクトルを評価できます：

```jldoctest ellipsoid_constructor
julia> σ(ones(3), E)
3-element Vector{Float64}:
 0.5773502691896258
 0.5773502691896258
 0.5773502691896258
```
