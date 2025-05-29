```
neighbor_sample(g, start, n=1; replace=false)
```

Draw random samples from neighbors from a given graph `g`. The weights for each edge on graph are considered to be proportional to the transition probability.

# Arguments

  * `g`: Data representing the graph topology. Possible type are

      * An adjacency matrix.
      * An `FeaturedGraph` or `SparseGraph` object.
  * `start::Int`: A vertex for a random neighbor sampling on graph `g`.
  * `n::Int`: Number of random neighbor sampling.
  * `replace::Bool`: Sample with replacement or not.

# Usage

```julia
julia> using GraphSignals

julia> adjm = [0 1 0 1 1;
               1 0 0 0 0;
               0 0 1 0 0;
               1 0 0 0 1;
               1 0 0 1 0];

julia> fg = FeaturedGraph(adjm);

julia> neighbor_sample(adjm, 1)
1-element Vector{Int64}:
 4

julia> neighbor_sample(fg, 1, 3)
3-element Vector{Int64}:
 5
 4
 2

julia> using Flux

julia> fg = fg |> gpu;

julia> neighbor_sample(fg, 4, 3, replace=true)
3-element Vector{Int64}:
 1
 5
 5
```

See also [`random_walk`](@ref)
