```
test_case(n::Source, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
test_case(n::NetworkNode, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
test_case(n::Storage, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
test_case(n::Sink, 𝒯::TimeStructure, warn_log; co2::ResourceEmit = ResourceEmit("CO₂", 1.0))
```

Default testset which tests that the developed [`Node`](@extref EnergyModelsBase.Node) `n` can be included in an `EnergyModelsBase` model, and that the resulting model is solvable.

The testset automatically identifies a minimum working case for the given node structure and solves this case. The [`Source`](@extref EnergyModelsBase.Source) node of the example has in all versions (except if you test a source node) a variable OPEX of 0. This implies, that if you test a [`Sink`](@extref EnergyModelsBase.Sink) node without a fixed demand, you must provide parameters so that it is beneficial to deliver energy to the sink node. This can be achieved through receiving a profit.

The same holds for a case in which you have a [`Storage`](@extref EnergyModelsBase.Storage) node without an output.

The following default values are chosen:

  * If we cannot use the function [`capacity`](@extref EnergyModelsBase.capacity), we use a capacity of 100. Otherwise, the capacity is sufficient for the capacity of the node.
  * If we cannot use the function [`opex_var`](@extref EnergyModelsBase.opex_var) (in all cases except for `n::Sink`), we assume it is 2500 for calculating the penalties of the Sink.

!!! warning "Potential problems with the function"
      * If you use `JuMP.fix` for fixing storage charge or discharge variables, that is not providing a new method for `has_input` or `has_output`, some of the tests may fail. These functions are in this case related to `:cap_use` of a source or sink, as well as `:stor_charge_use` or `:stor_discharge_use`.
      * The function is not working properly if you have the co2 keyword argument as `input` to your node.
      * The function is not designed to evaluate a required sequence of linked nodes. As an example, CCS retrofit requires the direct coupling of two nodes. This cannot be generalized.
      * The function cannot be used for a link as you would need to provide `Node`s as values for the fields `:from` and `:to`.


# Arguments

  * **`n::EMB.Node`** is the node that is tested.
  * **`𝒯::TimeStructure`** is the chosen time structure. It should only contain a single strategic period.
  * **`warn_log`** is the warning `NamedTuple` obtained through calling the function `compliance_element`.

# Keyword arguments

  * **`co2::ResourceEmit`** is the CO₂ resource in the model. If your node does not include CO₂, you do not have to specify it.

# Tests

  * The optimization problems leads to an optimal solution.
  * The variable `:cap_use` of all connected nodes is above 0.1 in at least one of the time periods.

!!! tip "Source, NetworkNode, and Sink"
    We test furthermore:

      * The variable `:cap_use` of the node `n` is above 0.1 in at least one of the time periods.


!!! note "Storage"
    `Storage` nodes use a random source variable OPEX and a fixed sink demand to analyse the changes in the storage level. This implies that if the `Storage` node does not have an output, then it is crucial that it is beneficial to store the `Resource`. This can be achieved through negative OPEX terms that must be above We test furthermore:

      * The variables `:stor_level`, `:stor_charge_use`, and `:stor_discharge_use` of the node `n` are above 0.1 in at least one of the time periods.

