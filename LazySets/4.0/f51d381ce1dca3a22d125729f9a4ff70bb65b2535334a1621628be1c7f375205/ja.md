```
ExponentialMap{N, S<:LazySet{N}} <: AbstractAffineMap{N, S}
```

指数写像の作用を表す型。

### フィールド

  * `spmexp` – スパース行列指数
  * `X`      – 集合

### ノート

指数写像は凸性を保持します：もし `X` が凸であれば、`X` の任意の指数写像も凸です。

### 例

`ExponentialMap` 型は、線形写像が遅延行列指数である場合、通常の乗算 (`*`) 演算子にオーバーロードされています。例えば：

```jldoctest constructors
julia> using SparseArrays

julia> A = sprandn(100, 100, 0.1);

julia> E = SparseMatrixExp(A);

julia> B = BallInf(zeros(100), 1.);

julia> M = E * B;  # 表す集合: exp(A) * B

julia> M isa ExponentialMap
true

julia> dim(M)
100
```

`ExponentialMap` を `ZeroSet` または `EmptySet` に適用すると、自動的に簡略化されます。

```jldoctest constructors
julia> E * ZeroSet(100)
ZeroSet{Float64}(100)

julia> E * EmptySet(100)
∅(100)
```
