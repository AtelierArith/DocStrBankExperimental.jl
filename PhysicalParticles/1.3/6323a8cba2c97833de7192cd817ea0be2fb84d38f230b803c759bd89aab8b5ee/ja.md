```
pconvert(a::Abstractay{T,1}) where T<:Number
```

二要素配列をPVector2Dに、三要素配列をPVectorに変換します。

## 例

```jl
julia> pconvert([1.0, 2.0])
PVector2D{Float64}(1.0, 2.0)

julia> pconvert([1.0, 2.0, 3.0])
PVector{Float64}(1.0, 2.0, 3.0)
```
