```
conc(v::AbstractVertex, vs::AbstractVertex...; dims, traitdecoration=identity, outwrap=identity)
conc(vname::AbstractString, v::AbstractVertex, vs::AbstractVertex...; dims, traitdecoration=identity, outwrap=identity)
```

Return a mutable vertex which concatenates input along dimension `dim`.

Use `traitdecoration` to attach other traits, such as [`named`](@ref), [`logged`](@ref) or [`validated`](@ref).

Use `outwrap=f` to wrap the concatenation function in `f`.

`conc(vname::AbstractString,...;traitdecoration = f, ...)` is equivalent to `conc(...;traitdecoration=named(vname) ∘ f, ...)`.

# Examples

```jldoctest
julia> using NaiveNASlib

julia> v = conc(inputvertex.(["in1", "in2", "in3"], 1:3)..., dims=1);

julia> nin(v)
3-element Vector{Int64}:
 1
 2
 3

julia> nout(v)
6

julia> v([1], [2, 3], [4, 5, 6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> v = conc(inputvertex.(["in1", "in2", "in3"], 1:3)..., dims=1, outwrap = f -> (x...) -> 2f(x...));
 
julia> v([1], [2, 3], [4, 5, 6])
6-element Vector{Int64}:
  2
  4
  6
  8
 10
 12
```
