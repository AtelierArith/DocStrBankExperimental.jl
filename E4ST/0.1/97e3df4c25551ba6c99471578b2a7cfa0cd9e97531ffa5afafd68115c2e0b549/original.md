```
abstract type Iterable
```

Sometimes, it may be desirable to run E4ST back-to-back with very similar sets of inputs, changing small things in the inputs between runs.  In order to do that, we have this custom interface!

The `Iterable` represents how [`run_e4st`](@ref) should iterate through multiple optimizations.  This structure could be used for any number of things, such as:

  * Running a sequence of years
  * Iterating to find the optimal price for natural gas to meet some load criterion.
  * Running the first simulation for capacity/retirement, then run the next sim to find generation with a higher temporal resolution.

## Adding an Iterable to config

  * Add the `Iterable` to the config, in the same way as you would add a `Modification` to the config file.  I.e.:

```yaml
# Inside config.yml
iter:
  type: MyIterType
  myfield: myval
```

## Interfaces

  * [`init!(iter::Iterable, config)`](@ref) - (optional) Initialize `iter` with `config`, making any changes.
  * [`issequential(iter)`](@ref) - (optional) returns whether or not the iterator will move forward in time sequentially.  Defaults to true so that the config can be reused for another simulation.
  * [`should_iterate(iter, config, data)`](@ref) - return whether or not the simulation should continue for another iteration.
  * [`iterate!(iter, config, data)`](@ref) - Makes any changes to any of the structures between iterations.
  * [`should_reread_data(iter)`](@ref) - Returns whether or not to reread the data when iterating.
  * [`fieldnames_for_yaml(::Type{<:Iterable})`](@ref) - (optional) return the fieldnames to print to yaml file in [`save_config`](@ref)
