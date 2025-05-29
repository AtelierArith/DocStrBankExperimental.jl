```
nodes_in_area(a::Area, ℒ::Vector{<:Link}; n_nodes=1000)
```

Returns a vector of all nodes in area `a` connected through links `ℒ`. The approach is based on a breadth-first-search and provides all connected nodes, contrary to the function [getnodesinarea](@ref).

# Arguments

  * **`a::Area`** is area that should be evaluated
  * **`ℒ::Vector{<:Link}`** is a vector of links that should be evaluated.

# Keyword arguments

  * **`n_nodes=1000`** the number of nodes added after which the loop is broken. It must be at least equal to the number of nodes in the area `a`.
