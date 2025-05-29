```
Tensor(arr, [init = zero(eltype(arr))])
```

Copy an array-like object `arr` into a corresponding, similar `Tensor` datastructure. Uses `init` as an initial value. May reuse memory when possible. To explicitly copy into a tensor, use @ref[`copyto!`].

# Examples

```jldoctest
julia> println(summary(Tensor(sparse([1 0; 0 1]))))
2×2 Tensor(Dense(SparseList(Element(0))))

julia> println(summary(Tensor(ones(3, 2, 4))))
3×2×4 Tensor(Dense(Dense(Dense(Element(0.0)))))
```
