```
struct Case <: AbstractCase
```

Type representing a case in `EnergyModelsBase`. It replaces the previously used dictionary for providing the input to a model.

# Fields

  * **`T::TimeStructure`** is the time structure of the model.
  * **`products::Vector{<:Resource}`** are the resources that should be incorporated into the model.

    !!! tip
        It must containt all [`ResourceEmit`](@ref) in `EnergyModelsBase`, but it is not necessary that the [`ResourceCarrier`](@ref) are included. It is however advisable to include all resources.
  * **`elements::Vector{Vector}`** are the vectors of [`AbstractElement`](@ref) that should be included in the analysis. It must contain at least vectors of nodes and links for an analysis to be useful.
  * **`couplings::Vector{Vector{Function}}`** are the couplings between the individual function element types. These elements are represented through a corresponding function, *e.g.*, [`get_nodes`](@ref) or [`get_links`](@ref).
  * **`misc::Dict`** is a dictionary that can be utilized for providing additional high level data in the existing format in the case of a new function for case creation. It is conditional through the application of a constructor.

!!! tip "Couplings"
    `EnergyModelsBase` requires the coupling of links and nodes. Hence, as a default approach, it adds the coupling

    ```julia
    couplings = [[get_nodes, get_links]]
    ```

    in an external constructor if the couplings are not specified.

