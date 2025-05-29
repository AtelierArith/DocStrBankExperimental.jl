```
numobs(data)
```

Return the total number of observations contained in `data`.

If `data` does not have `numobs` defined,  then in the case of `Tables.istable(data) == true` returns the number of rows, otherwise returns `length(data)`.

Authors of custom data containers should implement `Base.length` for their type instead of `numobs`. `numobs` should only be implemented for types where there is a difference between `numobs` and `Base.length` (such as multi-dimensional arrays).

`numobs` supports by default nested combinations of arrays, tuples, named tuples, and dictionaries. 

See also [`getobs`](@ref).

# Examples

```jldoctest
julia> x = (a = [1, 2, 3], b = ones(6, 3)); # named tuples

julia> numobs(x)
3

julia> x = Dict(:a => [1, 2, 3], :b => ones(6, 3)); # dictionaries

julia> numobs(x) 
3
```

All internal containers must have the same number of observations:

```julia
julia> x = (a = [1, 2, 3, 4], b = ones(6, 3));

julia> numobs(x)
ERROR: DimensionMismatch: All data containers must have the same number of observations.
Stacktrace:
 [1] _check_numobs_error()
   @ MLCore ~/.julia/dev/MLCore/src/observation.jl:176
 [2] _check_numobs
   @ ~/.julia/dev/MLCore/src/observation.jl:185 [inlined]
 [3] numobs(data::@NamedTuple{a::Vector{Int64}, b::Matrix{Float64}})
   @ MLCore ~/.julia/dev/MLCore/src/observation.jl:190
 [4] top-level scope
   @ REPL[13]:1
```
