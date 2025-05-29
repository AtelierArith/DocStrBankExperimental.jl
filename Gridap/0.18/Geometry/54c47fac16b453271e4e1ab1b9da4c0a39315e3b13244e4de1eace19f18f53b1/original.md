```
abstract type DiscreteModel{Dc,Dp} <: Grid
```

Abstract type holding information about a physical grid, the underlying grid topology, and a labeling of the grid faces. This is the information that typically provides a mesh generator, and it is what one needs to perform a simulation.

The `DiscreteModel` interface is defined by overloading the methods:

  * [`get_grid(model::DiscreteModel)`](@ref)
  * [`get_grid_topology(model::DiscreteModel)`](@ref)
  * [`get_face_labeling(g::DiscreteModel)`](@ref)

The interface is tested with this function:

  * [`test_discrete_model`](@ref)
