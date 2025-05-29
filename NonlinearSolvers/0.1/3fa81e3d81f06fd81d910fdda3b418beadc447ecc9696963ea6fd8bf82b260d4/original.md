```
NewtonsMethod(
        f!::F!,
        j!::J!,
        x_init::A,
    ) where {F! <: Function, J! <: Function, A <: AbstractArray}
```

A non-linear system of equations type.

# Fields

  * `f!`: Function to find the root of
  * `j!`: Jacobian of `f!`
  * `x_init`: Initial guess
  * `x1`: Storage
  * `J`: Storage
  * `J⁻¹`: Storage
  * `F`: Storage
