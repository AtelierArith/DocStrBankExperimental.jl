```
Model{Ny,Nx,Nc,T}
```

Abstract supertype of any model specification.

# Type parameters

  * `Ny::Int`: length of data vector `y`.
  * `Nx::Int`: number of *variable* parameters.
  * `Nc::Int`: number of linear coefficients.
  * `T <: Union{Float64, ComplexF64}` is equal to `eltype(y)`
