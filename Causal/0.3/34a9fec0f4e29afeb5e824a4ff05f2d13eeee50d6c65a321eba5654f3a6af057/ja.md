```julia
content(buf; flip)

```

`buf`の現在のデータを返します。`flip`が`true`の場合、返されるデータは反転されます。詳細は[`snapshot`](@ref)を参照してください。

# 例

```jldoctest
julia> buf = Buffer(5);

julia> write!(buf, 1:3)

julia> content(buf, flip=false)
3-element Array{Float64,1}:
 3.0
 2.0
 1.0

julia> buf = Buffer(2, 5);

julia> write!(buf, reshape(1:10, 2, 5))

julia> content(buf)
2×5 Array{Float64,2}:
 1.0  3.0  5.0  7.0   9.0
 2.0  4.0  6.0  8.0  10.0
```
