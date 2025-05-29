```
nb_fp_numbers(a::Floatmu{szE,szf}, b::Floatmu{szE,szf}) where {szE,szf}
```

Return the number of floats in the interval $[a,b]$. If $a > b$, throw an `ArgumentError` exception.

# Examples

```jldoctest
julia> nb_fp_numbers(Floatmu{2, 2}(-0.0),Floatmu{2, 2}(0.0))
1
julia> nb_fp_numbers(Floatmu{2, 2}(3.0),Floatmu{2, 2}(3.5))
2
```
