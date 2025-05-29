```
Bits{T} <: AbstractArray{Bool,1}
```

A mutable, statically-sized bit vector encoded in the bits in an element of type `T <: Integer`.

A `Bits` should behave similarly to a `BitVector`, but it is slightly faster as the size is known at compile-time to be `bitsize(T)`.
