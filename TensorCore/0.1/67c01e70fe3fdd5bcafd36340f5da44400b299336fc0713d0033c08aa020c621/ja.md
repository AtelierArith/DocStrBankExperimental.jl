```
hadamard(a, b)
a ⊙ b
```

配列 `a` と `b` に対して、要素ごとの乗算を行います。`a` と `b` は同一の `axes` を持っている必要があります。

`⊙` は高階関数に演算子として渡すことができます。

# 例

```jldoctest; setup=:(using TensorCore)
julia> a = [2, 3]; b = [5, 7];

julia> a ⊙ b
2-element Array{Int64,1}:
 10
 21

julia> a ⊙ [5]
ERROR: DimensionMismatch("Axes of `A` and `B` must match, got (Base.OneTo(2),) and (Base.OneTo(1),)")
[...]
```

`hadamard!(y, a, b)` も参照してください。
