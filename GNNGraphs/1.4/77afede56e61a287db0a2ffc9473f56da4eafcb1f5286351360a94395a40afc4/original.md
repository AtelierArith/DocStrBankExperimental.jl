```
rand_temporal_hyperbolic_graph(number_nodes::Int, 
                               number_snapshots::Int;
                               α::Real,
                               R::Real,
                               speed::Real,
                               ζ::Real=1,
                               self_loop = false,
                               kws...)
```

Create a random temporal graph given `number_nodes` nodes and `number_snapshots` snapshots. First, the positions of the nodes are generated with a quasi-uniform distribution (depending on the parameter `α`) in hyperbolic space within a disk of radius `R`. Two nodes are connected if their hyperbolic distance is less than `R`. Each following snapshot is created in order to keep the same initial distribution.

# Arguments

  * `number_nodes`: The number of nodes of each snapshot.
  * `number_snapshots`: The number of snapshots.
  * `α`: The parameter that controls the position of the points. If `α=ζ`, the points are uniformly distributed on the disk of radius `R`. If `α>ζ`, the points are more concentrated in the center of the disk. If `α<ζ`, the points are more concentrated at the boundary of the disk.
  * `R`: The radius of the disk and of connection.
  * `speed`: The speed to update the nodes.
  * `ζ`: The parameter that controls the curvature of the disk.
  * `self_loops`: If `true`, consider the node itself among its neighbors, in which               case the graph will contain self-loops.
  * `kws`: Further keyword arguments will be passed to the [`GNNGraph`](@ref) constructor of each snapshot.

# Example

```julia
julia> n, snaps, α, R, speed, ζ = 10, 5, 1.0, 4.0, 0.1, 1.0;

julia> thg = rand_temporal_hyperbolic_graph(n, snaps; α, R, speed, ζ)
TemporalSnapshotsGNNGraph:
  num_nodes: [10, 10, 10, 10, 10]
  num_edges: [44, 46, 48, 42, 38]
  num_snapshots: 5
```

# References

Section D of the paper [Dynamic Hidden-Variable Network Models](https://arxiv.org/pdf/2101.00414.pdf) and the paper  [Hyperbolic Geometry of Complex Networks](https://arxiv.org/pdf/1006.5169.pdf)
