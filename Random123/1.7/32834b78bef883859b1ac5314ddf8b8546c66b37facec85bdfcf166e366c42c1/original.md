```
threefry(key::NTuple{2,T}, ctr::NTuple{2,T}, ::Val{R})::NTuple{2,T}
threefry(key::NTuple{4,T}, ctr::NTuple{4,T}, ::Val{R})::NTuple{4,T}
```

Functional variant of [`Threefry2x`](@ref) and [`Threefry4x`](@ref).  Produces a pseudorandom output of type `T = UInt64` or `T = UInt32` from the inputs. This function if free of mutability and side effects.
