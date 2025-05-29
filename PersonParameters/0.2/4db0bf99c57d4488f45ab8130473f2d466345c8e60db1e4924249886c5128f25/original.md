```julia
modeltype(pp)

```

Get the scaling model used to calculate the person parameters in `pp`.

## Examples

```jldoctest
julia> pp = person_parameters(TwoPL, fill(zeros(3), 10), fill((a = 1.0, b = 0.0), 3), WLE());

julia> modeltype(pp)
TwoParameterLogisticModel
```
