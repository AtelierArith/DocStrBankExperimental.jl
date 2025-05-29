```
BoseFS{N,M,S} <: SingleComponentFockAddress
```

Address type that represents a Fock state of `N` spinless bosons in `M` modes by wrapping a [`BitString`](@ref), or a [`SortedParticleList`](@ref). Which is wrapped is chosen automatically based on the properties of the address.

# Constructors

  * `BoseFS{[N,M]}(val::Integer...)`: Create `BoseFS{N,M}` from occupation numbers. This is type-stable if the number of modes `M` and the number of particles `N` are provided. Otherwise, `M` and `N` are inferred from the arguments.
  * `BoseFS{[N,M]}(onr)`: Create `BoseFS{N,M}` from occupation number representation, see [`onr`](@ref). This is efficient if `N` and `M` are provided, and `onr` is a statically-sized collection, such as a `Tuple` or `SVector`.
  * `BoseFS{[N,M]}([M, ]pairs...)`: Provide the number of modes `M` and `mode => occupation_number` pairs. If `M` is provided as a type parameter, it should not be provided as the first argument.  Useful for creating sparse addresses. `pairs` can be multiple arguments or an iterator of pairs.
  * `BoseFS{N,M,S}(bs::S)`: Unsafe constructor. Does not check whether the number of particles in `bs` is equal to `N`.
  * [`@fs_str`](@ref): Addresses are sometimes printed in a compact manner. This representation can also be used as a constructor. See the last example below.

# Examples

```jldoctest
julia> BoseFS{6,5}(0, 1, 2, 3, 0)
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> BoseFS([abs(i - 3) ≤ 1 ? i - 1 : 0 for i in 1:5])
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> BoseFS(5, 2 => 1, 3 => 2, 4 => 3)
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> BoseFS{6,5}(i => i - 1 for i in 2:4)
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> fs"|0 1 2 3 0⟩"
BoseFS{6,5}(0, 1, 2, 3, 0)

julia> fs"|b 5: 2 3 3 4 4 4⟩"
BoseFS{6,5}(0, 1, 2, 3, 0)
```

See also: [`SingleComponentFockAddress`](@ref), [`OccupationNumberFS`](@ref), [`FermiFS`](@ref), [`CompositeFS`](@ref), [`FermiFS2C`](@ref).
