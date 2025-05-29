```
expmat(P::SimpleSparsePolynomialZonotope)
```

単純スパース多項式ゾノトープの指数の行列を返します。

### 入力

  * `P` – 単純スパース多項式ゾノトープ

### 出力

各列が多重次数である指数の行列。

### 注意事項

指数行列では、各行はパラメータ（数学的集合定義における $lpha_k$）に対応し、各列は単項式に対応します。

### 例

```jldoctest
julia> S = SimpleSparsePolynomialZonotope([2.0, 0], [1 2;2 2.], [1 4;1 2])
SimpleSparsePolynomialZonotope{Float64, Vector{Float64}, Matrix{Float64}, Matrix{Int64}}([2.0, 0.0], [1.0 2.0; 2.0 2.0], [1 4; 1 2])

julia> expmat(S)
2×2 Matrix{Int64}:
 1  4
 1  2
```
