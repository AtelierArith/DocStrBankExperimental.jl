```
LinearMap{N, S<:LazySet{N}, NM, MAT<:AbstractMatrix{NM}}
    <: AbstractAffineMap{N, S}
```

集合 $X$ の線形変換 $M⋅X$ を表す型です。

### フィールド

  * `M` – 行列/線形写像
  * `X` – 集合

### 注意事項

この型は線形写像の要素 `NM` に対してパラメトリックであり、ラップされた集合の数値型 (`N`) とは独立です。通常 `NM = N` ですが、例外がある場合もあります。例えば、`NM` が型 `N` の数値を保持する区間である場合、ここで `N` は `Float64` のような浮動小数点数型です。

線形写像は凸性を保持します：もし `X` が凸であれば、`X` の任意の線形写像もまた凸です。

### 例

例のために $3×2$ 行列と二次元の単位正方形を作成します。

```jldoctest constructors
julia> M = [1 2; 1 3; 1 4]; X = BallInf([0, 0], 1);
```

関数 $*$ は `LinearMap` オブジェクトを構築するためのエイリアスとして使用できます。

```jldoctest constructors
julia> lm = LinearMap(M, X)
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([1 2; 1 3; 1 4], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> lm2 = M * X
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([1 2; 1 3; 1 4], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> lm == lm2
true
```

便利のために、`M` は行列である必要はありません。ベクトル（$n×1$ 行列として解釈される）や `UniformScaling`、すなわちスカラー（スケーリング、すなわちスケーリングされた単位行列として解釈される）を使用することも許可されています。$1$ でのスケーリングは無視されます。

```jldoctest constructors
julia> using LinearAlgebra: I

julia> Y = BallInf([0], 1);  # 一次元区間

julia> [2, 3] * Y
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([2; 3;;], BallInf{Int64, Vector{Int64}}([0], 1))

julia> lm3 = 2 * X
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, SparseArrays.SparseMatrixCSC{Int64, Int64}}(sparse([1, 2], [1, 2], [2, 2], 2, 2), BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> 2I * X == lm3
true

julia> 1I * X == X
true
```

`LinearMap` オブジェクトに線形写像を適用すると、2つの写像が単一の `LinearMap` インスタンスに結合されます。再び、便利のために変換を利用できます。

```jldoctest constructors
julia> B = transpose(M); B * lm
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([3 9; 9 29], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> B = [3, 4, 5]; B * lm
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([12 38], BallInf{Int64, Vector{Int64}}([0, 0], 1))

julia> B = 2; B * lm
LinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([2 4; 2 6; 2 8], BallInf{Int64, Vector{Int64}}([0, 0], 1))
```

`LinearMap` を `ZeroSet` または `EmptySet` に適用すると、自動的に簡略化されます。

```jldoctest constructors
julia> M * ZeroSet{Int}(2)
ZeroSet{Int64}(3)

julia> M * EmptySet{Int}(2)
EmptySet{Int64}(3)
```
