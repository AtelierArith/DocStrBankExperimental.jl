```
@einsum [TensorType] expr
```

テンソル計算を[アインシュタインの総和規約](https://en.wikipedia.org/wiki/Einstein_notation)を使用して実行します。`@einsum`はテンソルの対称性を完全には推測できないため、返されるテンソル型に注釈を付けることが可能です（ただし、これは正しさがチェックされるわけではありません）。これにより、対称部分の計算を排除し、パフォーマンスを向上させることができます。

`expr`は無名関数であることができ、その場合、無名関数の引数は自由インデックスとして扱われます。引数が提供されない場合、自由インデックスは左から右に出現する順序に基づいて推測されます。

# 例

```jldoctest einsum
julia> A = rand(Mat{3,3});

julia> B = rand(Mat{3,3});

julia> (@einsum C[i,j] := A[j,k] * B[k,i]) ≈ (A * B)'
true

julia> (@einsum c := A[i,j] * A[i,j]) ≈ A ⋅ A
true

julia> (@einsum SymmetricSecondOrderTensor{3} D[i,j] := A[k,i] * A[k,j]) ≈ A' * A
true

julia> (@einsum (i,j) -> A[j,k] * B[k,i]) ≈ (A * B)'
true

julia> (@einsum A[i,j] * A[i,j]) ≈ A ⋅ A
true

julia> (@einsum SymmetricSecondOrderTensor{3} A[k,i] * A[k,j]) ≈ A' * A
true
```
