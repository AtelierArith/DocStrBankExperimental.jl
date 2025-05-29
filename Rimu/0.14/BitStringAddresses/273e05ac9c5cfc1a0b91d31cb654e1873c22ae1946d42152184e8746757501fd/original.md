```
OccupationNumberFS{M,T} <: SingleComponentFockAddress
```

Address type that stores the occupation numbers of a single component bosonic Fock state with `M` modes. The occupation numbers must fit into the type `T <: Unsigned`. The number of particles is runtime data, and can be retrieved with `num_particles(address)`.

# Constructors

  * `OccupationNumberFS(val::Integer...)`: Construct from occupation numbers. Must be < 256 to fit into `UInt8`.
  * `OccupationNumberFS{[M,T]}(onr)`: Construct from collection `onr` with `M` occupation numbers with type `T`. If unspecified, the type `T` of the occupation numbers is inferred from the type of the arguments.
  * `OccupationNumberFS(fs::BoseFS)`: Construct from [`BoseFS`](@ref).
  * With shortform macro [`@fs_str`](@ref). Specify the number of significant bits in braces. See example below.

# Examples

```jl_doctest
julia> ofs = OccupationNumberFS(1,2,3)
OccupationNumberFS{3, UInt8}(1, 2, 3)

julia> ofs == fs"|1 2 3⟩{8}"
true

julia> num_particles(ofs)
6
```
