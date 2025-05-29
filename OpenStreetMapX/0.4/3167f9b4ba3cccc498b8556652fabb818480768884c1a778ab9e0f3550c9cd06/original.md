```
a_star_algorithm(g::AbstractGraph{U},  
                s::Integer,                       
                t::Integer,                       
                distmx::AbstractMatrix{T}=Graphs.weights(g),
                heuristic::Function = (u,v) -> zero(T)) where {T, U}
```

High level function - implementation of A star search algorithm: (https://en.wikipedia.org/wiki/A**search*algorithm).  Based on the implementation in Graphs library,  however significantly improved in terms of performance.

**Arguments**

  * `g` : graph object
  * `S` : start vertex
  * `t` : end vertex
  * `distmx` : distance matrix
  * `heuristic` : search heuristic function; by default returns zero
