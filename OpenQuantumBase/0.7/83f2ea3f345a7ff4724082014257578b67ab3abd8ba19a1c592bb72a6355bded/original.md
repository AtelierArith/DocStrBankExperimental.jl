```julia
struct ODEParams
```

The `ODEParams` struct represents a complete set of parameters for an Ordinary  Differential Equation (ODE), including the Liouville operator, total evolution  time, an annealing parameter function, and an object storing accepted keyword  arguments for subroutines.

# Fields

  * `L`: Liouville operator
  * `tf`: Total evolution time
  * `annealing_parameter`: Function to convert physical time to annealing parameter
  * `accepted_kwargs`: Keyword arguments for subroutines
