```
setcoldata!(x, value)
```

Set the column annotations in `x` to `value`.

If `value` is a `DataFrame`, the first column should be called `"name"` and contain the column names of `x`; this can either be a `Vector{String}` or a `Vector{Nothing}` (if no column names are available).

If `value` is `nothing`, this is considered to be equivalent to a `DataFrame` with one `"name"` column containing `nothing`s.

The return value is a reference to the modified `x`.

# Examples

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> replacement = copy(coldata(x));

julia> replacement[!,"foobar"] = [ rand() for i in 1:size(x)[2] ];

julia> setcoldata!(x, replacement);

julia> names(coldata(x))
4-element Vector{String}:
 "name"
 "Treatment"
 "Response"
 "foobar"
```
