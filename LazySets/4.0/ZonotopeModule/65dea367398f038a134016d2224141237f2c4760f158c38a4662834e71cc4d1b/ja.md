```
Zonotope{N, VN<:AbstractVector{N}, MN<:AbstractMatrix{N}} <: AbstractZonotope{N}
```

ゾノトープを表す型。

### フィールド

  * `center`     – ゾノトープの中心
  * `generators` – 行列; 各列はゾノトープの生成子

### ノート

数学的に、ゾノトープは次の集合として定義されます。

$$
Z = \left\{ x ∈ ℝ^n : x = c + ∑_{i=1}^p ξ_i g_i,~~ ξ_i ∈ [-1, 1]~~ ∀ i = 1,…, p \right\},
$$

ここで、$c ∈ ℝ^n$ はその *中心* であり、$\{g_i\}_{i=1}^p$, $g_i ∈ ℝ^n$ は *生成子* の集合です。この特徴付けは、ゾノトープを線分の有限ミンコフスキー和として定義します。ゾノトープは、$ℝ^n$ における単位無限ノルムボールのアフィン変換による像として同等に記述できます。

ゾノトープは、生成子を行列として渡す方法、または各ベクトルが生成子を表すベクトルのリストを渡す方法の2つの異なる方法で構築できます。以下に両方の方法を示します。

### 例

与えられた中心と生成子の行列を持つ二次元ゾノトープ：

```jldoctest zonotope_label
julia> Z = Zonotope([1.0, 0.0], [0.1 0.0; 0.0 0.1])
Zonotope{Float64, Vector{Float64}, Matrix{Float64}}([1.0, 0.0], [0.1 0.0; 0.0 0.1])

julia> dim(Z)
2

julia> center(Z)
2-element Vector{Float64}:
 1.0
 0.0

julia> genmat(Z)
2×2 Matrix{Float64}:
 0.1  0.0
 0.0  0.1
```

ここで、`Zonotope` コンストラクタの最初のベクトルは中心に対応し、2番目の引数の各列は生成子に対応します。関数 `center` と `genmat` はそれぞれゾノトープの中心と生成子行列を返します。

`vertices_list` を使用して頂点を収集できます：

```jldoctest zonotope_label
julia> vertices_list(Z)
4-element Vector{Vector{Float64}}:
 [1.1, 0.1]
 [0.9, 0.1]
 [0.9, -0.1]
 [1.1, -0.1]
```

与えられた方向に沿ったサポートベクトルは `σ` を使用して計算できます（対応するサポート関数は `ρ` を使用して計算できます）：

```jldoctest zonotope_label
julia> σ([1.0, 1.0], Z)
2-element Vector{Float64}:
 1.1
 0.1
```

ゾノトープは、各ベクトルが生成子を表すベクトルのリストを受け取る代替コンストラクタを持っています：

```jldoctest
julia> Z = Zonotope(ones(2), [[1.0, 0.0], [0.0, 1.0], [1.0, 1.0]])
Zonotope{Float64, Vector{Float64}, Matrix{Float64}}([1.0, 1.0], [1.0 0.0 1.0; 0.0 1.0 1.0])

julia> genmat(Z)
2×3 Matrix{Float64}:
 1.0  0.0  1.0
 0.0  1.0  1.0
```
