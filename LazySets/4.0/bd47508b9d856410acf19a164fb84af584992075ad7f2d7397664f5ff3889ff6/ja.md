```
AffineMap{N, S<:LazySet{N}, NM, MAT<:AbstractMatrix{NM},
          VN<:AbstractVector{NM}} <: AbstractAffineMap{N, S}
```

集合 $X$ のアフィン変換 $M⋅X ⊕ v$ を表す型であり、すなわち集合

$$
Y = \{ y ∈ ℝ^n : y = Mx + v,\qquad x ∈ X \}.
$$

もし $X$ が $n$ 次元であれば、$M$ は $m × n$ 行列であり、$v$ は $m$ 次元のベクトルである必要があります。

### フィールド

  * `M` – 行列
  * `X` – 集合
  * `v` – 平行移動ベクトル

フィールドのゲッタ関数はそれぞれ `matrix`、`set`、`vector` です。

### 注意事項

アフィンマップは線形マップと平行移動の合成です。この型は線形マップの係数 `NM` にパラメトリックであり、ラップされた集合の数値型 `N` とは異なる場合があります。しかし、平行移動ベクトルの数値型は `NM` である必要があります。

アフィンマップは凸性を保持します：もし `X` が凸であれば、`X` の任意のアフィンマップも凸です。

### 例

例のために、$3×2$ 行列、二次元の単位正方形、および三次元ベクトルを作成します。それらを `AffineMap` に組み合わせます。

```jldoctest constructors
julia> A = [1 2; 1 3; 1 4]; X = BallInf([0, 0], 1); b2 = [1, 2]; b3 = [1, 2, 3];

julia> AffineMap(A, X, b3)
AffineMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}, Vector{Int64}}([1 2; 1 3; 1 4], BallInf{Int64, Vector{Int64}}([0, 0], 1), [1, 2, 3])
```

便宜上、`A` は行列である必要はなく、`UniformScaling` やスカラー（スケーリング、すなわちスケーリングされた単位行列として解釈される）を使用することも許可されています。$1$ でのスケーリングは無視され、純粋な `Translation` に簡略化されます。

```jldoctest constructors
julia> using LinearAlgebra

julia> am = AffineMap(2I, X, b2)
AffineMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Diagonal{Int64, Vector{Int64}}, Vector{Int64}}([2 0; 0 2], BallInf{Int64, Vector{Int64}}([0, 0], 1), [1, 2])

julia> AffineMap(2, X, b2) == am
true

julia> AffineMap(1, X, b2)
Translation{Int64, BallInf{Int64, Vector{Int64}}, Vector{Int64}}(BallInf{Int64, Vector{Int64}}([0, 0], 1), [1, 2])
```

`AffineMap` オブジェクトに線形マップを適用すると、2つのマップが新しい `AffineMap` インスタンスに結合されます。再び便宜上の変換を利用できます。

```jldoctest constructors
julia> B = [2 0; 0 2]; am2 = B * am
AffineMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}, Vector{Int64}}([4 0; 0 4], BallInf{Int64, Vector{Int64}}([0, 0], 1), [2, 4])

julia> 2 * am == am2
true
```

`AffineMap` を `ZeroSet` または `EmptySet` に適用すると、自動的に簡略化されます。

```jldoctest constructors
julia> AffineMap(A, ZeroSet{Int}(2), b3)
Singleton{Int64, Vector{Int64}}([1, 2, 3])

julia> AffineMap(A, EmptySet{Int}(2), b3)
EmptySet{Int64}(2)
```
