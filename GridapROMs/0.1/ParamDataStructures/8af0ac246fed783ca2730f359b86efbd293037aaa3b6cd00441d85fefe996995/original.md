```
struct Realization{P<:AbstractVector} <: AbstractRealization
  params::P
end
```

Represents standard parametric realizations, i.e. samples extracted from a given parameter space. The field `params` is most commonly a vector of vectors. When the parameters are scalars, they still need to be defined as vectors of vectors of unit length. In other words, we treat the case in which `params` is a vector of numbers as the case in which `params` is a vector of one vector.
