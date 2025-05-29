```
setpermstyle(format::Symbol)
```

Select the style in which permutations are displayed (in the REPL or in general as strings). This can be either

  * `:array` - as vector of integers whose $n$-th position represents the value at $n$), or
  * `:cycles` - as, more familiar for mathematicians, decomposition into disjoint cycles, where the value at $n$ is represented by the entry immediately following $n$ in a cycle (the default).

The difference is purely esthetical.

# Examples

```jldoctest
julia> setpermstyle(:array)
:array

julia> Perm([2,3,1,5,4])
[2, 3, 1, 5, 4]

julia> setpermstyle(:cycles)
:cycles

julia> Perm([2,3,1,5,4])
(1,2,3)(4,5)
```
