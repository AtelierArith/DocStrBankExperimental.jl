`two_tree(m)`

Given  a  square  matrix  `m`  with  zeroes  symmetric  with respect to the diagonal,  let  `G`  be  the  graph  with vertices `axes(m)[1]` and an edge between `i` and `j` iff `!iszero(m[i,j])`.

If  `G` is a line this function returns  it as a `Vector{Int}`. If `G` is a tree with one vertex `c` of valence `3` the function returns `(c,b1,b2,b3)` where  `b1,b2,b3` are  the branches  from this  vertex sorted by increasing length. Otherwise the function returns `nothing`.

This function is used when recognizing the type of a Cartan matrix.

```julia-repl
julia> two_tree(cartan(:A,4))
4-element Vector{Int64}:
 1
 2
 3
 4

julia> two_tree(cartan(:E,8))
(4, [2], [3, 1], [5, 6, 7, 8])
```
