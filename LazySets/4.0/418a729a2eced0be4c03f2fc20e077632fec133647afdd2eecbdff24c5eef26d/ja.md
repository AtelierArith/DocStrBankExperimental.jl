```
ExponentialProjectionMap{N, S<:LazySet{N}} <: AbstractAffineMap{N, S}
```

スパース行列の指数関数の射影を集合に適用することを表す型です。

### フィールド

  * `spmexp` – スパース行列の指数関数の射影
  * `X`      – 集合

### ノート

指数関数の射影は凸性を保持します：もし `X` が凸であれば、`X` の任意の指数関数の射影も凸です。

### 例

次の例では、占有確率 $0.5$ の $6 × 6$ のランダムスパース射影行列を使用し、無限ノルムにおける2D単位球に適用します：

```jldoctest
julia> using SparseArrays

julia> R = sparse([5, 6], [1, 2], [1.0, 1.0]);

julia> L = sparse([1, 2], [1, 2], [1.0, 1.0], 2, 6);

julia> using ExponentialUtilities

julia> A = sprandn(6, 6, 0.5);

julia> E = SparseMatrixExp(A);

julia> M = ProjectionSparseMatrixExp(L, E, R);

julia> B = BallInf(zeros(2), 1.0);

julia> X = ExponentialProjectionMap(M, B);

julia> dim(X)
2
```
