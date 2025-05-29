```
fs"$(string)"
```

Parse the compact representation of a Fock state. Useful for copying the printout from a vector to the REPL.

# Example

```jldoctest
julia> DVec(BoseFS{3,4}(0, 1, 2, 0) => 1)
DVec{BoseFS{3, 4, BitString{6, 1, UInt8}},Int64} with 1 entry, style = IsStochasticInteger{Int64}()
  fs"|0 1 2 0⟩" => 1

julia> fs"|0 1 2 0⟩" => 1 # Copied from above printout
BoseFS{3,4}(0, 1, 2, 0) => 1

julia> fs"|1 2 3⟩⊗|0 1 0⟩" # composite bosonic Fock state
CompositeFS(
  BoseFS{6,3}(1, 2, 3),
  BoseFS{1,3}(0, 1, 0),
)

julia> fs"|↑↓↑⟩" # construct a fermionic Fock state
CompositeFS(
  FermiFS{2,3}(1, 0, 1),
  FermiFS{1,3}(0, 1, 0),
)

julia> s = fs"|0 1 2 0⟩{}" # constructing OccupationNumberFS with default UInt8 container
OccupationNumberFS{4, UInt8}(0, 1, 2, 0)

julia> [s] # prints out with the signifcant number of bits specified in braces
1-element Vector{OccupationNumberFS{4, UInt8}}:
 fs"|0 1 2 0⟩{8}"
```

See also [`FermiFS`](@ref), [`BoseFS`](@ref), [`CompositeFS`](@ref), [`FermiFS2C`](@ref), [`OccupationNumberFS`](@ref).
