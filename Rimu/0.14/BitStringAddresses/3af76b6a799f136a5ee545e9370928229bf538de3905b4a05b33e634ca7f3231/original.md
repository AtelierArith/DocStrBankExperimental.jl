```
excitation(addr::OccupationNumberFS, c::NTuple, d::NTuple)
→ (nadd, α)
```

Generate an excitation on an [`OccupationNumberFS`](@ref) by applying the creation and destruction operators specified by the tuples of mode numbers `c` and `d` to the Fock state `addr`. The modes are indexed by integers (starting at 1), or by indices of type `BoseFSIndex`. The value of `α` is given by the square root of the product of mode occupations before destruction and after creation.

The number of particles may change by this type of excitation.

# Example

```jl_doctest
julia> s = fs"|1 2 3⟩{8}"
OccupationNumberFS{3, UInt8}(1, 2, 3)

julia> num_particles(s)
6

julia> es, α = excitation(s, (1,1), (3,))
(OccupationNumberFS{3, UInt8}(3, 2, 2), 4.242640687119285)

julia> num_particles(es)
7
```
