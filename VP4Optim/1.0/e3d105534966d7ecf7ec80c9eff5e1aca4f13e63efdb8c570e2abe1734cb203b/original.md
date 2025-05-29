```
y!(mod::Model{Ny,Nx,Nc,T}, new_y::AbstractArray) where {Ny,Nx,Nc,T}
```

Sets new data values.

## Default

  * Resets `mod.y::SVector{Ny, T}` with the content of `new_y`.
  * Calculates the squared magnitude of `mod.y` and stores the result in `mod.y2::Float64`.
  * Returns nothing.

## Remarks

  * In most cases, it is safer to call [set_data!](@ref set_data!) instead of [y!](@ref y!).
