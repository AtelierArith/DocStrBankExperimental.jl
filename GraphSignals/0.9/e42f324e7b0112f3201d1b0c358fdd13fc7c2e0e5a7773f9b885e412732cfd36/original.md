```
random_walk(g, start, n=1)
```

Draw random walk samples from a given graph `g`. The weights for each edge on graph are considered to be proportional to the transition probability.

# Arguments

  * `g`: Data representing the graph topology. Possible type are

      * An adjacency matrix.
      * An `FeaturedGraph` or `SparseGraph` object.
  * `start::Int`: A start point for a random walk on graph `g`.
  * `n::Int`: Number of random walk steps.

# Usage

```julia
julia> using GraphSignals

julia> adjm = [0 1 0 1 1;
               1 0 0 0 0;
               0 0 1 0 0;
               1 0 0 0 1;
               1 0 0 1 0];

julia> fg = FeaturedGraph(adjm);

julia> random_walk(adjm, 1)
1-element Vector{Int64}:
 5

julia> random_walk(fg, 1, 3)
3-element Vector{Int64}:
 5
 4
 4

julia> using Flux

julia> fg = fg |> gpu;

julia> random_walk(fg, 4, 3)
3-element Vector{Int64}:
 1
 1
 1
```

See also [`neighbor_sample`](@ref)
