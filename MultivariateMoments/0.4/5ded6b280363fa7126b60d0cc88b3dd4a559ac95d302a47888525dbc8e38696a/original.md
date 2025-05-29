```
dirac(X::AbstractVector{<:AbstractMoment}, s::AbstractSubstitution...)
```

Creates the dirac measure by evaluating the moments of `X` using `s`.

## Examples

Calling `dirac([x*y, x*y^2], x=>3, y=>2)` should the measure with moment `x*y` of value `6` and moment `x*y^2` of value `12`.
