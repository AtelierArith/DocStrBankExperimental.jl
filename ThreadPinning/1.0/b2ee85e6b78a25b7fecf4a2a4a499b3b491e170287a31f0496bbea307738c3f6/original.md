```
with_pinthreads(f::F, args...;
    soft = false,
    kwargs...
)
```

Runs the function `f` with the specified pinning and restores the previous thread affinities afterwards. Typically to be used in combination with do-syntax.

By default (`soft=false`), before the thread affinities are restored, the Julia threads will be pinned to the CPU-threads they were running on previously.

**Example**

```julia
julia> getcpuids()
4-element Vector{Int64}:
  7
 75
 63
  4

julia> with_pinthreads(:cores) do
           getcpuids()
       end
4-element Vector{Int64}:
 0
 1
 2
 3

julia> getcpuids()
4-element Vector{Int64}:
  7
 75
 63
  4
```
