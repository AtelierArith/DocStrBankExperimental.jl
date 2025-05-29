```
KeyedArray(A; i=2:3, j=["a", "b"])
NamedDimsArray(A; i=2:3, j=["a", "b"])
```

これらのコンストラクタは `KeyedArray(NamedDimsArray(A, names), keys)` または `NamedDimsArray(KeyedArray(A, keys), names)` を作成し、同等であるべきです。

これらは `wrapdims(A; kw...)` よりも少ないサニティチェックを行います。

# 例

```jldoctest
julia> KeyedArray(reshape(1:12,3,4), row=[:a, :b, :c], iter=10:10:40)
2次元 KeyedArray(NamedDimsArray(...)) with keys:
↓   row ∈ 3-element Vector{Symbol}
→   iter ∈ 4-element StepRange{Int64,...}
データは、3×4 reshape(::UnitRange{Int64}, 3, 4) で eltype Int64:
        (10)  (20)  (30)  (40)
  (:a)     1     4     7    10
  (:b)     2     5     8    11
  (:c)     3     6     9    12

julia> ans[iter=3]
1次元 KeyedArray(NamedDimsArray(...)) with keys:
↓   row ∈ 3-element Vector{Symbol}
データは、3-element Vector{Int64}:
 (:a)  7
 (:b)  8
 (:c)  9
```
