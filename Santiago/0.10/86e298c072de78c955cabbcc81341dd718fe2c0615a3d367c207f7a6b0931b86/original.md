```julia
properties_dataframe(
    systems::Array{Santiago.System};
    massflow_selection
) -> Any

```

Extract systems properties into a `DataFrame`.

With the argument `massflow_selection` we can select which information should be extracted from the massflow calulation.

Note, massflows per technology ('tech_flows') cannot be export to a Dataframe! Try the JSON export.

### Example:

`massflow_selection = ["recovered | water | mean", "lost | water| air loss | q_0.5"]` This will extract the mean value of the recovered water and the 50% quantile of the water lost to air. Note, the order of the values must match the dimensions of the  `NamedArray` stored in the system propertes!

`massflow_selection` can be set to `"all"` extrace all massflow quantities (which are a lot!).
