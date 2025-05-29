```julia
struct StateCache{M, JointCollection} <: RigidBodyDynamics.AbstractTypeDict
```

A container that manages the creation and storage of [`MechanismState`](@ref) objects of various scalar types, associated with a given `Mechanism`.

A `StateCache` can be used to write generic functions that use `MechanismState` objects, while avoiding overhead due to the construction of a new `MechanismState` with a given scalar type every time the function is called.

# Examples

```julia-repl
julia> mechanism = rand_tree_mechanism(Float64, Revolute{Float64}, Prismatic{Float64}, QuaternionFloating{Float64});

julia> cache = StateCache(mechanism)
StateCache{…}

julia> state32 = cache[Float32]
MechanismState{Float32, Float64, Float64, …}(…)

julia> cache[Float32] === state32
true

julia> cache[Float64]
MechanismState{Float64, Float64, Float64, …}(…)
```
