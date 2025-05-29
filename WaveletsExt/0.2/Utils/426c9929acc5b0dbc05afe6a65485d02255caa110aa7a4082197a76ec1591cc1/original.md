```
getchildindex(idx, child)
```

Get the child index of a parent index `idx`.

# Arguments

  * `idx::T where T<:Integer`: Index of parent node.
  * `child::Symbol`: Type of child. For binary trees, available children are `:left` and `:right`. For quadtrees, available children are `:topleft`, `:topright`, `:bottomleft`, `:bottomright`.

# Returns

  * `::T`: Index of child node.

# Examples

```repl
using WaveletsExt

getchildindex(3,:left) == 6
getchildindex(3,:right) == 7
getchildindex(3,:topleft) == 22
getchildindex(3,:topright) == 23
getchildindex(3,:bottomleft) == 24
getchildindex(3,:bottomright) == 25
```
