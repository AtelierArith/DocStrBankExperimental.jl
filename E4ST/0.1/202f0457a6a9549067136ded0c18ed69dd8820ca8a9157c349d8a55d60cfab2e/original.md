```
const RPS = GenerationStandard{:RPS}
```

**Renewable Portfolio Standard** - A policy that constrains a certain amount of load from a region to be supplied by qualifying clean/renewable energy. 

RPS is defined as an alias of GenerationStandard where the default crediting type is StandardRPSCrediting. mod_rank for RPS will be 1.0 because that is the rank of GenerationStandards

## Fields

  * `name` - Name of the policy
  * `targets` - The yearly targets for the RPS
  * `crediting` - the crediting structure and related fields. Standard CES crediting is CreditingByBenchmark.
  * `gen_filters` - Filters on which generation qualifies to fulfill the RPS. Sometimes qualifying generators may be outside of the RPS load region if they supply power to it.
  * `load_bus_filters` - Filters on which buses fall into the RPS load region. The RPS will be applied to the load from these buses.

[`GenerationStandard`](@ref)
