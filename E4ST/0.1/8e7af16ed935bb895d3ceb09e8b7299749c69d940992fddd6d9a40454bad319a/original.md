```
abstract type Crediting
```

Crediting is used to set the credit levels of generators for policies. It is primarily used for [`GenerationStandard`](@ref)s and [`ReserveRequirement`](@ref)s (RPS, CES, carveouts, etc). 

## Setup inside config yaml

Crediting is specified in the yaml file. A type key must be specified, along with the approriate keys for the credit type you specified. Two examples are shown in the config below.

```yaml
base_out_path:    "../out/3bus_rps"
mods:
  example_rps:
    type: "RPS"
    crediting: 
      type: "StandardRPSCrediting"
    gen_filters:
      bus_nation: "archenland"
    load_targets:
      stormness_rps:
        filters:
          state: stormness
        targets:
          y2035: 0.85
          y2040: 0.9
  example_rps_gentype:
    type: "RPS"
    crediting: 
      type: "CreditByGentype"
      credits:
        solar: 0.8
        wind: 1.0
        oswind: 1.0
    gen_filters:
      bus_nation: "narnia"
    load_targets:
      narnia_rps:
        targets:
          y2030: 0.7
          y2035: 0.8
          y2040: 0.9
        filters:  
          nation: "narnia"
  stor:
    type: Storage
    file: "../data/3bus/storage.csv"


```

## Standard Crediting subtypes include:

  * [`CreditByBenchmark`](@ref)
  * [`CreditByGentype`](@ref)

## Interfaces Implements

  * [`get_credit(c::Crediting, data, gen_row::DataFrameRow)`](@ref) - gets the appropriate credit level for the generator row for the given Crediting subtype.
