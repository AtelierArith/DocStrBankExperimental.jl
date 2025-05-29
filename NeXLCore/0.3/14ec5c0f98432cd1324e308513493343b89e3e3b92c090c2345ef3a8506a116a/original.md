```
η(::Type{<:BackscatterCoefficient}, mat::Material, e0::Float64) = #
η(elm::Element, e0::Real)
```

Models are: Tomlin1963, LoveScott1978η, Pouchou1991η, August1989η, Reimer1998

The default backscatter coefficient algorith is August1989η.
