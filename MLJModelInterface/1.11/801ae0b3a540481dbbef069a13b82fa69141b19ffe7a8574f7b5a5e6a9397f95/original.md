```
scitype(X)
```

The scientific type (interpretation) of `X`, distinct from its machine type.

### Examples

```julia-repl
julia> scitype(3.14)
Continuous

julia> scitype([1, 2, missing])
AbstractVector{Union{Missing, Count}} 

julia> scitype((5, "beige"))
Tuple{Count, Textual}

julia> using CategoricalArrays

julia> X = (gender = categorical(['M', 'M', 'F', 'M', 'F']),
            ndevices = [1, 3, 2, 3, 2]);

julia> scitype(X)
Table{Union{AbstractVector{Count}, AbstractVector{Multiclass{2}}}}
```
