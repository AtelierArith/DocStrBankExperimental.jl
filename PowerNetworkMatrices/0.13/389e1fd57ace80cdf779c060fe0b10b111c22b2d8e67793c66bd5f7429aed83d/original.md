```julia
IncidenceMatrix(sys)

```

Builds the Incidence matrix of the system by evaluating the actual matrix and other relevant values.

# Arguments

  * `sys::PSY.System`:       the PowerSystem system to consider
  * `reduce_radial_branches::Bool`:       if True the matrix will be evaluated discarding       all the radial branches and leaf buses (optional, default value is false)
