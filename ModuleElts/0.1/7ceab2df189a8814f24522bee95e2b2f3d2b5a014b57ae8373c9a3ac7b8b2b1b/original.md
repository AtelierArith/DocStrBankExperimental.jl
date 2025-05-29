`ModuleElt{K,V}`  has a  similar interface  to `Dict{K,V}`,  but instead of assuming  that `K` is hashable, it assumes  that `K` is sortable. This also has the advantage that ModuleElts are naturally sortable.

The  only field, a `Vector{Pair{K,V}}`, is  kept sorted by `K`; by default, the  constructor checks sorting, adds values with the same key, and deletes keys with zero value. This can be overriden with the keyword `check=false`.
