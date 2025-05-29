```
compliance_element(n::EMB.Node)
compliance_element(n::Storage)
compliance_element(l::Link)
```

Returns two `NamedTuple`s corresponding to respectively the errors and warnings of the testing of the indivdiual test functions. The called test functions are dependent on the chosen type:

!!! note "Node"
    The following functions are called:

      * [`compliance_capacity`](@ref), not for `Storage` nodes,
      * [`compliance_opex_var`](@ref), not for `Storage` nodes,
      * [`compliance_opex_fixed`](@ref), not for `Storage` nodes,
      * [`compliance_inputs`](@ref), if the node has an input, checked through the function [`has_input`](@extref EnergyModelsBase.has_input),
      * [`compliance_outputs`](@ref), if the node has an output, checked through the function [`has_output`](@extref EnergyModelsBase.has_output),
      * [`compliance_data`](@ref),
      * [`compliance_level`](@ref) for `Storage` nodes, including a check that the `level` is corresponding to an [`AbstractStorageParameters`](@extref EnergyModelsBase.AbstractStorageParameters), and
      * [`compliance_stor_res`](@ref) for `Storage` nodes.


!!! tip "Link"
    `Link`s are more flexible than `Node`s. As a consequence, we do not check whether the access functions are working. Instead, it is checked whether `Link`s have the fields `:from` and `:to` and that either of them is restricted to a n.

