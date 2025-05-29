```
Rule
```

A `Rule` object contains the information required to apply an `applyrule` method to every cell of every timestep of a simulation.

The [`applyrule`](@ref) method follows the form:

```julia
@inline applyrule(data::AbstractSimData, rule::MyRule, state, I::Tuple{Int,Int}) = ...
```

Where `I` is the cell index, and `state` is a single value, or a `NamedTuple` if multiple grids are requested. the [`AbstractSimData`](@ref) object can be used to access  current timestep and other simulation data and metadata.

Rules can be updated from the original rule before each timestep, in [`modifyrule`](@ref). Here a paremeter depends on the sum of a grid:

```jldoctest
using DynamicGrids, Setfield
struct MySummedRule{R,W,T} <: CellRule{R,W}
    gridsum::T
end
function modifyrule(rule::MySummedRule{R,W}, data::AbstractSimData) where {R,W}
    Setfield.@set rule.gridsum = sum(data[R])
end

# output
modifyrule (generic function with 1 method)
```

Rules can also be run in sequence, as a `Tuple` or in a [`Ruleset`](@ref)s.

DynamicGrids guarantees that:

  * `modifyrule` is run once for every rule for every timestep.   The result is passed to `applyrule`, but not retained after that.
  * `applyrule` is run once for every rule, for every cell, for every timestep, unless an   optimisation like [`SparseOpt`](@ref) is used to skip empty cells.
  * the output of running a rule for any cell does not affect the input of the   same rule running anywhere else in the grid.
  * rules later in the sequence are passed grid state updated by the earlier rules.
  * masked areas, and wrapped or removed `boundary` regions are updated between rules when   they have changed.

## Multiple grids

The keys of the init `NamedTuple` will be match the grid keys used in `R` and `W` for each rule, which is a type like `Tuple{:key1,:key1}`. Note that the names are user-specified, and should never be fixed by a `Rule`.

Read grid names are retrieved from the type here as `R1` and `R2`, while write grids are `W1` and `W2`.

```jldoctest
using DynamicGrids
struct MyMultiSetRule{R,W} <: SetCellRule{R,W} end
function applyrule(
    data::AbstractSimData, rule::MyMultiSetRule{Tuple{R1,R2},Tuple{W1,W2}}, (r1, r2), I
) where {R1,R2,W1,W2}
    add!(data[W1], 1, I) 
    add!(data[W2], 1, I) 
end

# output
applyrule (generic function with 1 method)
```

The return value of an `applyrule` is written to the current cell in the specified `W` write grid/s. `Rule`s writing to multiple grids simply return a `Tuple` in the order specified by the `W` type params.

## Rule Performance

Rules may run many millions of times during a simulation. They need to be fast. Some basic guidlines for writing rules are:

  * Never allocate memory in a `Rule` if you can help it.
  * Type stability is essential. [`isinferred`](@ref) is useful to check   if your rule is type-stable.
  * Using the `@inline` macro on `applyrule` can help force inlining your   code into the simulation.
  * Reading and writing from multiple grids is expensive due to additional load   on fast cahce memory. Try to limit the number of grids you use.
  * Use a graphical profiler, like ProfileView.jl, to check your rules overall   performance when run with `sim!`.
