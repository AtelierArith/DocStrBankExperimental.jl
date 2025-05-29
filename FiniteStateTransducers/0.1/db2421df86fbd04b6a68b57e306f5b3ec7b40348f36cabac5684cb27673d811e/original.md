`BFS(fst,initial)`

Returns an iterator that performs a breadth-first search (BFS) of `fst` starting from the state `initial`.

At each iteartion the tuple `(i,p)` is returned, where `i` is the current state and `p` a [`Path`](@ref).
