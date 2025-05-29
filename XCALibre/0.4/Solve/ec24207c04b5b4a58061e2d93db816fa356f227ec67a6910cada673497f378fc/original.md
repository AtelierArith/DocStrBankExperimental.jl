```
struct JacobiSmoother{L,F,V} <: AbstractSmoother
    loops::L
    omega::F
    x_temp::V
end
```

Structure to hold information for using the weighted Jacobi smoother. 

# Fields

  * `loops` represents the number of smoothing iterations.
  * `omega` represents the relaxation weight, 1 corresponds to no weighting. Typically a weight of 2/3 is used to filter high frequencies in the residual field.
  * `x_temp` is a vector used internally to store intermediate solutions.

# Constructors

```
JacobiSmoother(mesh::AbstractMesh)
```

This constructor takes a mesh object as input to create the smoother. The number of cells in the mesh is used to allocate `x_temp`. The number of loops and smoother factor are set to 5 and 1, respectively.

```
JacobiSmoother(; domain, loops, omega=2/3)
```

Alternative constructor for `JacobiSmoother`.

# keyword arguments

  * `domain` represents a mesh object of type `AbstractMesh`.
  * `loops` is the number of iterations to be used
  * `omega` represents the weighting factor, 1 does not relax the system, 2/3 is found to work well for smoothing high frequencies in the residual field
