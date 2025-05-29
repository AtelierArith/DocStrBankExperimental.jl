```
setrowdata!(x, value)
```

Set the row annotations in `x` to `value`.

If `value` is a `DataFrame`, the first column should be called `"name"` and contain the row names of `x`; this can either be an `AbstractVector{AbstractString}` or a `Vector{Nothing}` (if no row names are available).

If `value` is `nothing`, this is considered to be equivalent to a `DataFrame` with one `"name"` column containing `nothing`s.

The return value is a reference to the modified `x`.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> # using DataFrames

julia> replacement = copy(rowdata(x));

julia> replacement[!,"foobar"] = [ rand() for i in 1:size(x)[1] ];

julia> setrowdata!(x, replacement);

julia> names(rowdata(x))
3-element Vector{String}:
 "name"
 "Type"
 "foobar"
```
