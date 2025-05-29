Convenience macro for flanking code with [`Marker.startregion`](@ref) and [`Marker.stopregion`](@ref) on all threads separately.

# Examples

```julia
julia> using LIKWID

julia> Marker.init()

julia> @parallelmarker begin
           Threads.@thread :static for i in 1:Threads.nthreads()
               # thread-local computation
           end
       end

julia> Marker.close()

```
