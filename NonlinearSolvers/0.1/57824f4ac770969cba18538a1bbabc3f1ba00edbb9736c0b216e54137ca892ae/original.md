```
NewtonsMethodAD(f!::F!, x_init::A) where {F!, A <: AbstractArray}
```

A non-linear system of equations type.

# Fields

  * `f!`: Function to find the root of
  * `x_init`: Initial guess
  * `x1`: Storage
  * `J`: Storage
  * `J⁻¹`: Storage
  * `F`: Storage
