```
AbstractDomain
```

An abstract super type for any domain type. A domain type `D <: AbstractDomain` must implement the following methods to properly interface `AbstractDomain`.

  * `Base.∈(val, ::D)`
  * `Base.rand(::D)`
  * `Base.length(::D)` that is the number of elements in a discrete domain, and the distance between bounds or similar for a continuous domain

Additionally, if the domain is used in a dynamic context, it can extend

  * `add!(::D, args)`
  * `delete!(::D, args)`

where `args` depends on `D`'s structure
