```
Solvers
```

Structure used to define the collection of discretization methods for transport calculations associated with each of the particle and additionnal coupled transport informations.

# Mandatory field(s)

  * `methods_list::Vector{Discrete_Ordinates}` : list of the particle methods
  * `maximum_number_of_generations::Int64` : number of particle generations to transport.

# Optional field(s) - with default values

  * N/A
