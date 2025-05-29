```
AbstractSimData
```

Supertype for simulation data objects. Thes hold [`GridData`](@ref),  [`SimSettings`](@ref) and other objects needed to run the simulation,  and potentially required from within rules.

An `AbstractSimData` object is accessable in [`applyrule`](@ref) as the first parameter.

Multiple grids can be indexed into using their key if you need to read from arbitrary locations:

```julia
funciton applyrule(data::AbstractSimData, rule::SomeRule{Tuple{A,B}},W}, (a, b), I) where {A,B,W}
    grid_a = data[A]
    grid_b = data[B]
    ...
end
```

In single-grid simulations `AbstractSimData` objects can be indexed directly as  if they are a `Matrix`.

## Methods

  * `currentframe(data)`: get the current frame number, an `Int`
  * `currenttime(data)`: the current frame time, which `isa eltype(tspan)`
  * `aux(data, args...)`: get the `aux` data `NamedTuple`, or `Nothing`.   adding a `Symbol` or `Val{:symbol}` argument will get a field of aux.
  * `tspan(data)`: get the simulation time span, an `AbstractRange`.
  * `timestep(data)`: get the simulaiton time step.
  * `boundary(data)` : returns the [`BoundaryCondition`](@ref) - `Remove` or `Wrap`.
  * `padval(data)` : returns the value to use as grid border padding.

These are also available, but you probably shouldn't use them and their behaviour is not guaranteed in furture versions. Using them will also mean a rule is useful  only in specific contexts, which is discouraged.

  * `settings(data)`: get the simulaitons [`SimSettings`](@ref) object.
  * `extent(data)` : get the simulation [`AbstractExtent`](@ref) object.
  * `init(data)` : get the simulation init `AbstractArray`/`NamedTuple`
  * `mask(data)` : get the simulation mask `AbstractArray`
  * `source(data)` : get the `source` grid that is being read from.
  * `dest(data)` : get the `dest` grid that is being written to.
  * `radius(data)` : returns the `Int` radius used on the grid,   which is also the amount of border padding.
