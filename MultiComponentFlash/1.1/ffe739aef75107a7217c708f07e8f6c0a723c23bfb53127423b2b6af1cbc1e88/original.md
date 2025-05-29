```
flash_storage(eos, [c]; <keyword arguments>)
```

Pre-allocate storage for `flash_2ph!`.

# Arguments

  * `eos`: the equation-of-state to be used for the flash
  * `c`: conditions for the mixture. Types in conditions must match later usage (e.g. for use with ForwardDiff).

# Keyword arguments

  * `method = SSIFlash()`: Flash method to use. Can be `SSIFlash()`, `NewtonFlash()` or `SSINewtonFlash()`.
  * `static_size = false`: Use `SArrays` and `MArrays` for fast flash, but slower compile times.
  * `inc_jac`: Allocate storage for Newton/Jacobian. Required for Newton (and defaults to `true` for that method) or for `diff_externals`.
  * `diff_externals = false`: Allocate storage for matrix inversion required to produce partial derivatives of flash using `set_partials`.

See also: [`flash_2ph!`](@ref) [`set_partials`](@ref)
