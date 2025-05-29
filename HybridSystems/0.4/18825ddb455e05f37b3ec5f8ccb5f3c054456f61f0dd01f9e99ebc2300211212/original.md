```
HybridSystem{A, S, R, W, SV<:AbstractVector{S}, RV<:AbstractVector{R}, RW<:AbstractVector{W}} <: AbstractHybridSystem
```

A hybrid system modelled as a hybrid automaton.

### Fields

  * `automaton`  – hybrid automaton of type `A`.
  * `modes`      – vector of modes of type `S` indexed by the discrete states,                 both the domain and the dynamic are stored in this field.                 See [`stateset`](@ref) to access the domain.
  * `resetmaps`  – vector of reset maps of type `R` indexed by the label of the                 transition, the guard is stored as constraint of the map in                 this field. See [`stateset`](@ref) to access the guard.
  * `switchings` – vector of switchings of type `W` indexed by the label of the                 transition, see [`AbstractSwitching`](@ref).
  * `ext`        – dictionary that can be used by extensions.

### Notes

The automaton `automaton` of type `A` models the different discrete states and the allowed transitions with corresponding labels.

The mode dynamic and domain are stored in a continuous dynamical system of type `S` in the vector `modes`. They are indexed by the discrete states of the automaton.

The reset maps and guards are given as a map or a discrete dynamical system of type `R` in the vector `resetmaps`. They are indexed by the labels of the corresponding transition.

The switching of type `W` is given in the `switchings` vector, indexed by the label of the transition.

Additional data can be stored in the `ext` field.

### Examples

See [the Thermostat example](https://github.com/blegat/HybridSystems.jl/blob/master/examples/Thermostat.ipynb).
