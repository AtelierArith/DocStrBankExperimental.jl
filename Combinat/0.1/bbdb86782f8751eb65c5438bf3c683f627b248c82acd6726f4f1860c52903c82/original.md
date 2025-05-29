`tally(v;dict=false)`

counts how many times each element of collection or iterable `v` occurs and returns a sorted `Vector` of `elt=>count` (a variant of StatsBase.countmap).  By default the  elements of `v`  must be sortable; if they  are not but hashable, giving the keyword `dict=true` uses a `Dict` to build (much slower) an unsorted result.

```julia-repl
julia> tally("a tally test")
7-element Vector{Pair{Char, Int64}}:
 ' ' => 2
 'a' => 2
 'e' => 1
 'l' => 2
 's' => 1
 't' => 3
 'y' => 1
```
