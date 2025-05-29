```
EquivalentPosition{T}
```

3Dの対称操作の表現で、行列の乗算と加算によって定義されます。

## 例

```jldoctest
julia> eq = parse(EquivalentPosition, "1-x, z, y+1/2")
-x+1,z,y+1/2

julia> eq([1//3, 0, 1//4])
3-element StaticArrays.SVector{3, Rational{Int64}} with indices SOneTo(3):
 2//3
 1//4
 1//2
```

型パラメータ `T` は、対称操作を格納するために使用される数値型です。通常は `Rational{Int}` または `Float64` のいずれかであるべきです。
