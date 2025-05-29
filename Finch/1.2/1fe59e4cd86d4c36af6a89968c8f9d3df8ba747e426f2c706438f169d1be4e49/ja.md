```
Tensor(arr, [init = zero(eltype(arr))])
```

配列のようなオブジェクト `arr` を対応する類似の `Tensor` データ構造にコピーします。`init` を初期値として使用します。可能な場合はメモリを再利用します。テンソルに明示的にコピーするには、@ref[`copyto!`] を使用してください。

# 例

```jldoctest
julia> println(summary(Tensor(sparse([1 0; 0 1]))))
2×2 Tensor(Dense(SparseList(Element(0))))

julia> println(summary(Tensor(ones(3, 2, 4))))
3×2×4 Tensor(Dense(Dense(Dense(Element(0.0)))))
```
