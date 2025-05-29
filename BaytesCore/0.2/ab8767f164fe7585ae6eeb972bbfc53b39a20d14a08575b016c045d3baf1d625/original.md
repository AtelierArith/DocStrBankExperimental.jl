```julia
mutable struct ValueHolder{T<:Real}
```

Mutable struct to hold a single scalar value that can be stored and updated in immutable structs.

# Fields

  * `current::Real`: Scalar value
