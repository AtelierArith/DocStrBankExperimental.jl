```
Reformer <: AbstractReformer
```

A network node with start-up and shut-down time and costs that should be used for reformer technology descriptions.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per capacity usage.
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity.
  * **`input::Dict{<:Resource, <:Real}`** are the input [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`output::Dict{<:Resource, <:Real}`** are the produced [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`data::Array{Data}`** is an array of additional data (e.g., for investments).
  * **`load_limits::LoadLimits`** are limits on the utilization load of the electrolyser. [`LoadLimits`](@ref) can provide both lower and upper limits on the actual load.
  * **`startup::CommitParameters`** are parameters for the startup state constraints.
  * **`shutdown::CommitParameters`** are parameters for the shutdown state constraints.
  * **`offline::CommitParameters`** are parameters for the offline state constraints.
  * **`ramp_limit::AbstractRampParameters`** are the limit on the allowable change in the capacity usage.

!!! note
      * If you introduce CO₂ capture through the application of [`CaptureEnergyEmissions`](@extref EnergyModelsBase.CaptureEnergyEmissions), you have to add your CO₂ instance as output. The reason for this is that we declare the variable `:output` through the `output` dictionary.
      * The specified startup, shutdown, and offline costs are relative to the installed capacity and a duration of 1 of an operational period.
      * The rate limit is relative to the installed capacity and a duration of 1 of an operational period.

