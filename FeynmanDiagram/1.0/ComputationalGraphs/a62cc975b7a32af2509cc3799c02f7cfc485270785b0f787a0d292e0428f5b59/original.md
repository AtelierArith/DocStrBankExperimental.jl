```
multi_product(graphs::Vector{Graph{F,W}}, constants::AbstractVector=ones(F, length(graphs))) where {F,W,C}
```

Construct a product graph from multiple input graphs, where each graph can be weighted by a constant.  For graphs that are repeated more than once, it adds a power operator to the subgraph to represent the repetition. Moreover, it optimizes any trivial unary operators in the resulting product graph.

# Arguments:

  * `graphs::Vector{Graph{F,W}}`: A vector of input graphs to be multiplied.
  * `constants::AbstractVector`: A vector of scalar multiples. If not provided, it defaults to a vector of ones of the same length as `graphs`.

Returns:

  * A new product graph with the unique subgraphs (or powered versions thereof) and the associated constants as subgraph factors.

# Example:

```
Given graphs `g1`, `g2`, `g1` and constants `c1`, `c2`, `c3`, the function computes `(c1*c3)*(g1)^2 * c2*g2`.
```
