```julia
BA_Matrix(sys; reduce_radial_branches)

```

Build the BA matrix from a given System

# Arguments

  * `sys::PSY.System`:       PSY system for which the matrix is constructed
  * `reduce_radial_branches::Bool`:       if True the matrix is build considering radial branches removed from       the system
