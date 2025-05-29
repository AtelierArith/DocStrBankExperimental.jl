```
HydroStor(
    id::Any,
    rate_cap::TimeProfile,
    stor_cap::TimeProfile,
    level_init::TimeProfile,
    level_inflow::TimeProfile,
    level_min::TimeProfile,
    opex_var::TimeProfile,
    opex_fixed::TimeProfile,
    stor_res::ResourceCarrier,
    input,
    output,
    Data,
)
```

Legacy constructor for a regulated hydropower plant without pumping capabilities. This version will be discontinued in the near future and replaced with the new version of `HydroStor{StorageBehavior}` in which the parametric input defines the behavior of the hydropower plant. In addition, the introduction of `AbstractStorageParameters` allows for an improved description of the individual capacities and OPEX contributions for the storage `level` and `discharge` capacity.

See the *[documentation](https://energymodelsx.github.io/EnergyModelsRenewableProducers.jl/stable/how-to/update-models/#Adjustments-from-0.4.0-to-0.6.x)* for further information regarding how you can translate your existing model to the new model.

## Fields

  * **`id`** is the name/identifyer of the node.
  * **`rate_cap::TimeProfile`** is the installed installed rate capacity.
  * **`stor_cap::TimeProfile`** is the installed storage capacity in the dam.
  * **`level_init::TimeProfile`** is the initial stored energy in the dam.
  * **`level_inflow::TimeProfile`** is the inflow of power per operational period.
  * **`level_min::TimeProfile`** is the minimum fraction of the reservoir capacity that has to remain in the `HydroStorage` node.
  * **`opex_var::TimeProfile`** are the variable operational expenses per GWh produced.
  * **`opex_fixed::TimeProfile`** are the fixed operational costs of the storage caacity.
  * **`stor_res::ResourceCarrier`** is the stored `Resource`.
  * **`input::Dict{Resource, Real}`** are the stored and used resources. The values in the Dict are ratios describing the energy loss when using the pumps.
  * **`output::Dict{Resource, Real}`** can only contain one entry, the stored resource.
  * **`data::Array{Data}`** additional data (e.g. for investments). This value is conditional through the application of a constructor.
