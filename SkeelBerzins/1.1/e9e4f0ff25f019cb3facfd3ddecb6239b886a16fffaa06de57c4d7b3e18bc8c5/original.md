```
ODEFunction(problem)
```

Generate an [ODEFunction](https://docs.sciml.ai/DiffEqDocs/stable/types/ode_types/#SciMLBase.ODEFunction) from the spatial discretization derived in the [`SkeelBerzins.assemble!`](@ref) function. It is expressed as a [mass matrix ODE](https://docs.sciml.ai/DiffEqDocs/stable/tutorials/dae_example/) if the mass matrix is different from the identity matrix or as a simple [system of ODEs](https://docs.sciml.ai/DiffEqDocs/stable/tutorials/advanced_ode_example/#stiff) otherwise and defines the problem with respect to the sparsity pattern.

Input argument:

  * `problem`: Structure of type [`SkeelBerzins.ProblemDefinition`](@ref).
