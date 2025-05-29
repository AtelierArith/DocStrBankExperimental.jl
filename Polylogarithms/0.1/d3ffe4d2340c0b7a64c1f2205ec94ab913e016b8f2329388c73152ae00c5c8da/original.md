```
harmonic(x::ComplexOrReal{Float64})
```

Calculates harmonic numbers extended to non-integer arguments using the  digamma form.

## Arguments

  * $x$ `::ComplexOrReal{Float64}`: index of the Harmonic number to calculate

## Examples

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2.0)
1.5000000000000016
```
