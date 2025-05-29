```
DeltaArray(V::AbstractVector)
```

`V`を対角成分とする行列を構築します。

関連情報は[`delta`](@ref)を参照してください。

# 例

```jldoctest
julia> DeltaArray([1, 10, 100])
3×3 DeltaArray{Int64, 2, Vector{Int64}}:
 1   0    0
 0  10    0
 0   0  100
```
