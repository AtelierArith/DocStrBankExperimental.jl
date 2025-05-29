Convenience macro for flanking code with [`Marker.startregion`](@ref) and [`Marker.stopregion`](@ref).

# Examples

```julia
julia> using LIKWID

julia> Marker.init()

julia> @marker "sleeping..." sleep(1)
true

julia> @marker "create rand vec" rand(100)
true

julia> Marker.close()

```
