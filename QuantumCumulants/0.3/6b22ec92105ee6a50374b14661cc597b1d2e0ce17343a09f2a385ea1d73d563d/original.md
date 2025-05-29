```
cumulant_expansion(avg, order::Int)
```

For an [`average`](@ref) of an operator, expand it in terms of moments up to `order` neglecting their joint cumulant.

See also: https://en.wikipedia.org/wiki/Cumulant#Joint_cumulants

# Examples

```
julia> avg = average(a*b)
⟨a*b⟩

julia> cumulant_expansion(avg,1)
(⟨a⟩*⟨b⟩)

julia> avg = average(a*b*c)
⟨a*b*c⟩

julia> cumulant_expansion(avg,2)
((⟨a*b⟩*⟨c⟩)+(⟨a*c⟩*⟨b⟩)+(⟨a⟩*⟨b*c⟩)+(-2*⟨a⟩*⟨b⟩*⟨c⟩))
```

# Optional arguments

*simplify=true: Specify whether the result should be simplified. *kwargs...: Further keyword arguments being passed to simplification.
