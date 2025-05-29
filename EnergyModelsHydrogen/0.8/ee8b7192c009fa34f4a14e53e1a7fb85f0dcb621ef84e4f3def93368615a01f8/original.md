```
Electrolyzer <: AbstractElectrolyzer
```

Description of an electrolyzer node with minimum and maximum load as well as degredation and stack replacement.

New fields: `min_load`, `max_load`, `stack_lifetime`, `stack_replacement_cost`, and `degradation_rate`.

# Fields

  * **`id`** is the name/identifier of the node.
  * **`cap::TimeProfile`** is the installed capacity.
  * **`opex_var::TimeProfile`** is the variable operating expense per capacity used (through the variable `:cap_use`).
  * **`opex_fixed::TimeProfile`** is the fixed operating expense per installed capacity.
  * **`input::Dict{<:Resource, <:Real}`** are the input [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`output::Dict{<:Resource, <:Real}`** are the produced [`Resource`](@extref EnergyModelsBase.Resource)s with conversion value `Real`.
  * **`data::Vector{Data}`** is the additional data (e.g. for investments).
  * **`load_limits::LoadLimits`** are limits on the utilization load of the electrolyser. [`LoadLimits`](@ref) can provide both lower and upper limits on the actual load.
  * **`degradation_rate::Real`** is the percentage drop in efficiency due to degradation in %/1000 h.
  * **`stack_replacement_cost::TimeProfile`** is the replacement cost of electrolyzer stacks.
  * **`stack_lifetime::Real`** is the total operational stack life time.

!!! note
      * The nominal electrolyzer efficiency is captured through the combination of `input` and `output`.
      * The fixed and variable operating expenses are always related to installed capacity and its usage. This implies if you define the capacity *via* the input through a value of 1, then the variable operating expense is calaculated through the required electricity.
      * Stack replacement can only be done once a strategic period, in the first operational period. The thought process behind is that it would otherwise lead to issues if a strategic period is repeated.

