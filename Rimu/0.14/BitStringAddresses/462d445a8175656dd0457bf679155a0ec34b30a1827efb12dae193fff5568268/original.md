```
FermiFS2C <: AbstractFockAddress
FermiFS2C(onr_a, onr_b)
```

Fock state address with two fermionic (spin) components. Alias for [`CompositeFS`](@ref) with two [`FermiFS`](@ref) components. Construct by specifying either two compatible [`FermiFS`](@ref)s, two [`onr`](@ref)s, or the number of modes followed by `mode => occupation_number` pairs, where `occupation_number=1` will put a particle in the first component and `occupation_number=-1` will put a particle in the second component. See examples below.

# Examples

```jldoctest
julia> FermiFS2C(FermiFS(1,0,0), FermiFS(0,1,1))
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)

julia> FermiFS2C((1,0,0), (0,1,1))
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)

julia> FermiFS2C(3, 1 => 1, 2 => -1, 3 => -1)
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)

julia> fs"|↑↓↓⟩"
CompositeFS(
  FermiFS{1,3}(1, 0, 0),
  FermiFS{2,3}(0, 1, 1),
)
```
