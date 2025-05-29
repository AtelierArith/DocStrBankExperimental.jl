```
map_main(f,args...;kwargs...)
```

Like `map(f,args...)` but only apply `f` to one component of the arrays in `args`.

# Optional key-word arguments

  * `main = MAIN`: The linear index of the component to map
  * `otherwise = (args...)->nothing`: The function to apply when mapping indices different from `main`.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> a = [1,2,3,4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> map_main(-,a,main=2)
4-element Vector{Union{Nothing, Int64}}:
   nothing
 -2
   nothing
   nothing
```
