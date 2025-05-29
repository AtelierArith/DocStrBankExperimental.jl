# Build all systems from a given the sources and and a set of technologies.

```
build_systems(sources::Array{T},
              technologies::Array{T};
              additional_sources::Array{T}=T[]
              addlooptechs::Bool=true, looptechgroup=[:S, :T],
              max_candidates=10_000_000) where T <: AbstractTech
```

## Parameters

  * sources:            An array of sources technologies
  * technologies:       Array of sanitation technologies
  * additional_sources: Array of source technolgies that are all added to the main sources (such as kitch sink)
  * max_candidates:     The maximal number of system extensions that are tried.                     A small number may lead to faster computations, but only to a random subset                     of all possible systems in generated.

## Values

An array of all found sanitation systems.
