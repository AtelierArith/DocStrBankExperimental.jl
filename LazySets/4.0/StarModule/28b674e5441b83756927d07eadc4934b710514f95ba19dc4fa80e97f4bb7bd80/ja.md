```
Star{N, VN<:AbstractVector{N}, MN<:AbstractMatrix{N}, PT<:AbstractPolyhedron{N}} <: AbstractPolyhedron{N}
```

多面体の述語を持つ一般化された星集合、すなわち

$$
X = \{x ∈ ℝ^n : x = x₀ + ∑_{i=1}^m α_i v_i,~~\textrm{s.t. } P(α) = ⊤ \},
$$

ここで $x₀ ∈ ℝ^n$ は中心であり、$m$ 個のベクトル $v₁, …, vₘ$ は星集合の基底を形成し、組み合わせ係数 $α = (α₁, …, αₘ) ∈ ℝ^m$ は述語の決定変数、すなわち $P : α ∈ ℝ^m → \{⊤, ⊥\}$ であり、ポリヘドロンの述語は $P(α) = ⊤$ が成り立つのは、ある固定の $A ∈ ℝ^{p × m}$ と $b ∈ ℝ^p$ に対して $A·α ≤ b$ が成り立つ場合に限る。

### フィールド

  * `c` – 中心を表すベクトル
  * `V` – 各列が基底ベクトルに対応する行列
  * `P` – 述語を表す多面体集合

### 注意事項

述語関数は線形制約の論理積として実装されており、すなわち `AbstractPolyhedron` のサブタイプです。表記のわずかな乱用により、述語は $P(α) = ⊤$ が成り立つような $ℝ^n$ の部分集合を示すためにも使用されます。

$$
m
$$

個の基底ベクトル（それぞれ $n$ 次元）は、$n × m$ 行列の列として格納されます。

`Star` は数学的に多面体集合 `P` のアフィン写像に等しいことに注意してください。変換行列と平行移動ベクトルはそれぞれ `V` と `c` です。

ここで定義された星集合は [DuggiralaV16](@citet) で導入されました。予備的な定義については [BakD17](@citet) も参照してください。

### 例

この例は [2] の例1から引用されています。二次元平面 $ℝ^2$ を考えます。次のようにします。

```jldoctest star_constructor
julia> V = [[1.0, 0.0], [0.0, 1.0]];
```

基底ベクトルとし、

```jldoctest star_constructor
julia> c = [3.0, 3.0];
```

星集合の中心とします。述語を半径1の無限ノルムボールとします。

```jldoctest star_constructor
julia> P = BallInf(zeros(2), 1.0);
```

次のように星集合 $X = ⟨c, V, P⟩$ を構築します。

```jldoctest star_constructor
julia> S = Star(c, V, P)
Star{Float64, Vector{Float64}, Matrix{Float64}, BallInf{Float64, Vector{Float64}}}([3.0, 3.0], [1.0 0.0; 0.0 1.0], BallInf{Float64, Vector{Float64}}([0.0, 0.0], 1.0))
```

各コンポーネントフィールドのゲッタ関数を使用できます。

```jldoctest star_constructor
julia> center(S)
2-element Vector{Float64}:
 3.0
 3.0

julia> basis(S)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

julia> predicate(S)
BallInf{Float64, Vector{Float64}}([0.0, 0.0], 1.0)
```

この場合、上記の一般化された星 $S$ は以下の長方形 $T$ に等しいです。

$$
    T = \{(x, y) ∈ ℝ^2 : (2 ≤ x ≤ 4) ∧ (2 ≤ y ≤ 4) \}
$$
