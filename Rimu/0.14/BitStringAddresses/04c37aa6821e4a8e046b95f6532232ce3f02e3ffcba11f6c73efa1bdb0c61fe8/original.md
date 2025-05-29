```
FermiFS{N,M,S} <: SingleComponentFockAddress
```

Address type that represents a Fock state of `N` fermions of the same spin in `M` modes by wrapping a [`BitString`](@ref), or a [`SortedParticleList`](@ref). Which is wrapped is chosen automatically based on the properties of the address.

# Constructors

  * `FermiFS{[N,M]}(val::Integer...)`: Create `FermiFS{N,M}` from occupation numbers. This is type-stable if the number of modes `M` and the number of particles `N` are provided. Otherwise, `M` and `N` are inferred from the arguments.
  * `FermiFS{[N,M]}(onr)`: Create `FermiFS{N,M}`  from occupation number representation, see [`onr`](@ref). This is efficient if `N` and `M` are provided, and `onr` is a statically-sized collection, such as a `Tuple{M}` or `SVector{M}`.
  * `FermiFS{[N,M]}([M, ]pairs...)`: Provide the number of modes `M` and pairs of the form `mode => 1`. If `M` is provided as a type parameter, it should not be provided as the first argument.  Useful for creating sparse addresses. `pairs` can be multiple arguments or an iterator of pairs.
  * `FermiFS{N,M,S}(bs::S)`: Unsafe constructor. Does not check whether the number of particles in `bs` is equal to `N`, or whether each mode only contains one particle.
  * [`@fs_str`](@ref): Addresses are sometimes printed in a compact manner. This representation can also be used as a constructor. See the last example below.

# Examples

```jldoctest
julia> FermiFS{3,5}(0, 1, 1, 1, 0)
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> FermiFS([abs(i - 3) ≤ 1 for i in 1:5])
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> FermiFS(5, 2 => 1, 3 => 1, 4 => 1)
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> FermiFS{3,5}(i => 1 for i in 2:4)
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> fs"|⋅↑↑↑⋅⟩"
FermiFS{3,5}(0, 1, 1, 1, 0)

julia> fs"|f 5: 2 3 4⟩"
FermiFS{3,5}(0, 1, 1, 1, 0)
```

See also: [`SingleComponentFockAddress`](@ref), [`BoseFS`](@ref), [`CompositeFS`](@ref), [`FermiFS2C`](@ref), [`BitString`](@ref), [`OccupationNumberFS`](@ref).
