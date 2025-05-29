```
matching_map(
    a₊::Dict, a₋::Dict, matcher;
    ds::DynamicalSystem, p, pprev, next_id
) → rmap
```

Given dictionaries `a₊, a₋` mapping IDs to values, return a *replacement map*: a dictionary mapping the IDs (keys) in dictionary `a₊` to IDs (keys) in dictionary `a₋`, so that so that values in `a₊` that are the "closest" to values in `a₋` get assigned the same key as in `a₋`. In this way keys of `a₊` are "matched" to keys of `a₋`. Use [`swap_dict_keys`](@ref) to apply `rmap` to `a₊` or to other dictionaries with same keys as `a₊`.

How matching happens, i.e., how "closeness" is defined, depends on the algorithm `matcher`.

The values contained in `a₊, a₋` can be anything supported by `matcher`. Within Attractors.jl they are typically `StateSpaceSet`s representing attractors. Typically the +,- mean after and before some change of parameter of a dynamical system.

`matching_map` always returns an empty dictionary of either `a₊, a₋` is empty.

## Keyword arguments

  * `ds`: the dynamical system that generated `a₊, a₋`.
  * `p, pprev`: the parameters corresponding to `a₊, a₋`. Both need to be iterables mapping parameter index to parameter value (such as `Dict, Vector{Pair}`, etc., so whatever can be given as input to `DynamicalSystems.set_parameters!`).
  * `next_id = next_free_id(a₊, a₋)`: the ID to give to values of  `a₊` that cannot be matched to `a₋` and hence must obtain a new unique ID.

Some matchers like [`MatchBySSSetDistance`](@ref) do not utilize `ds, p, pprev` in any way while other matchers like [`MatchByBasinEnclosure`](@ref) do, and those require expliticly giving values to `ds, p, pprev` as their default values is just `nothing`.
