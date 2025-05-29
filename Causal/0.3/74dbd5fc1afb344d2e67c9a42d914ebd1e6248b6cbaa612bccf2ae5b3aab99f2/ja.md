```julia
write!(buf, val)

```

`vals`の各列を`buf`に書き込みます。

!!! warning バッファモードは、データがバッファに書き込まれる方法を決定します。バッファモードについては、[`Normal`](@ref)、[`Cyclic`](@ref)、[`Lifo`](@ref)、[`Fifo`](@ref)も参照してください。

# 例

```jldoctest
julia> buf = Buffer(5)
5-element Buffer{Cyclic,Float64,1}

julia> write!(buf, 1.)
1.0

julia> write!(buf, [2, 3])

julia> buf.internals
2-element Array{Array{Float64,1},1}:
 [3.0, 2.0, 1.0, 0.0, 0.0]
 [2.0, 1.0, 0.0, 0.0, 0.0]

julia> buf = Buffer(2,5)
2×5 Buffer{Cyclic,Float64,2}

julia> write!(buf, [1, 1])
2-element Array{Int64,1}:
 1
 1

julia> write!(buf, [2 3; 2 3])

julia> buf.internals
2-element Array{Array{Float64,2},1}:
 [3.0 2.0 … 0.0 0.0; 3.0 2.0 … 0.0 0.0]
 [2.0 1.0 … 0.0 0.0; 2.0 1.0 … 0.0 0.0]
```
