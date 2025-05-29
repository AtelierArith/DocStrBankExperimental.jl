```
struct GenerationStandard{T} <: Policy
```

A generation standard (also refered to as a portfolio standard) is a constraint on generation where a portion of generation from certain generators must meet the a portion of the load in a specified region. This encompasses RPSs, CESs, and technology carveouts. To assign the credit (the portion of generation that can contribute) to generators, the [`Crediting`](@ref) type is used.

  * `name` - Name of the policy
  * `gen_filters` - Filters on which generation qualifies to fulfill the GS. Sometimes qualifying generators may be outside of the GS load region if they supply power to it.
  * `crediting` - the crediting structure and related fields
  * `load_targets` - OrderedDict containing key-value pairs where each key is the name of a requirement (not currently used), and each value is an OrderedDict with the following keys:

      * `filters` - Filters on which buses fall into the GS load region. The GS will be applied to the load from these buses.
      * `targets` - The yearly percent targets of the qualifying load that must be covered by the qualifying generation.
