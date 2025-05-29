```julia
algorithm(pp)

```

Get the algorithm used to calculate the person parameters in `pp`.

## Examples

```jldoctest
julia> pp = person_parameters(OnePL, fill(zeros(3), 5), zeros(3), MLE());

julia> algorithm(pp)
MLE{Roots.Secant}(Roots.Secant())
```
