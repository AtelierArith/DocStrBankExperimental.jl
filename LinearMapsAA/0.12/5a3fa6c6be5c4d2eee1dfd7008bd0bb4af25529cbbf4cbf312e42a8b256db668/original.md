```
struct LinearMapAX{T,Do,Di,LM,P}
```

Union of `LinearMapAM` and `LinearMapAO` because most operations apply to both AM and AO types.

  * `T` : `eltype`
  * `Do` : output dimensionality
  * `Di` : input dimensionality
  * `LM` : `LinearMap` type
  * `P` : `NamedTuple` type
