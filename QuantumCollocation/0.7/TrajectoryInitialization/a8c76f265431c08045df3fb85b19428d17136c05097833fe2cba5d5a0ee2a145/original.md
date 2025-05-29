```
unitary_geodesic(U_init, U_goal, times; kwargs...)
```

Compute the geodesic connecting U*init and U*goal at the specified times. Allows for the possibility of unequal times and ranges outside [0,1].

# Arguments

  * `U_init::AbstractMatrix{<:Number}`: The initial unitary operator.
  * `U_goal::AbstractMatrix{<:Number}`: The goal unitary operator.
  * `times::AbstractVector{<:Number}`: The times at which to evaluate the geodesic.

# Keyword Arguments

  * `return_unitary_isos::Bool=true`: If true returns a matrix where each column is a unitary isovec, i.e. vec(vcat(real(U), imag(U))). If false, returns a vector of unitary matrices.
  * `return_generator::Bool=false`: If true, returns the effective Hamiltonian generating the geodesic.
