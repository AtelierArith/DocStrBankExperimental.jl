```
ConcreteFeaturedGraph(fg; nf=node_feature(fg), ef=edge_feature(fg),
                      gf=global_feature(fg), pf=positional_feature(fg))
```

This is a syntax sugar for construction for `FeaturedGraph` and `FeaturedSubgraph` object. It is an idempotent operation, which gives the same type of object as inputs. It wraps input `fg` again but reconfigures with `kwargs`.

# Arguments

  * `fg`: `FeaturedGraph` and `FeaturedSubgraph` object.
  * `nf`: Node features.
  * `ef`: Edge features.
  * `gf`: Global features.
  * `pf`: Positional features.

# Usage

```jldoctest
julia> using GraphSignals

julia> adjm = [0 1 1 1;
               1 0 1 0;
               1 1 0 1;
               1 0 1 0];

julia> nf = rand(10, 4);

julia> fg = FeaturedGraph(adjm; nf=nf)
FeaturedGraph:
	Undirected graph with (#V=4, #E=5) in adjacency matrix
	Node feature:	ℝ^10 <Matrix{Float64}>

julia> ConcreteFeaturedGraph(fg, nf=rand(7, 4))
FeaturedGraph:
    Undirected graph with (#V=4, #E=5) in adjacency matrix
    Node feature:	ℝ^7 <Matrix{Float64}>
```
