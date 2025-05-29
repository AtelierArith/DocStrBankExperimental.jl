```
freqtable(x::AbstractVector...;
          skipmissing::Bool = false,
          weights::AbstractVector{<:Real} = UnitWeights(),
          subset::Union{Nothing, AbstractVector{Int}, AbstractVector{Bool}} = nothing])

freqtable(t, cols::Union{Symbol, AbstractString}...;
          skipmissing::Bool = false,
          weights::AbstractVector{<:Real} = UnitWeights(),
          subset::Union{Nothing, AbstractVector{Int}, AbstractVector{Bool}} = nothing])
```

Create frequency table from vectors or table columns.

`t` can be any type of table supported by the [Tables.jl](https://github.com/JuliaData/Tables.jl) interface.

**Examples**

```jldoctest
julia> freqtable([1, 2, 2, 3, 4, 3])
4-element Named Array{Int64,1}
Dim1  │ 
──────┼──
1     │ 1
2     │ 2
3     │ 2
4     │ 1

julia> df = DataFrame(x=[1, 2, 2, 2], y=[1, 2, 1, 2]);

julia> freqtable(df, :x, :y)
2×2 Named Array{Int64,2}
x ╲ y │ 1  2
──────┼─────
1     │ 1  0
2     │ 1  2

julia> freqtable(df, :x, :y, subset=df.x .> 1)
1×2 Named Array{Int64,2}
x ╲ y │ 1  2
──────┼─────
2     │ 1  2

```
