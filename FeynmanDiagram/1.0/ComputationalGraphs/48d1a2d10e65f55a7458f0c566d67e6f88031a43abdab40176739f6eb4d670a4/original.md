```
function linear_combination(graphs::Vector{Graph{F,W}}, constants::AbstractVector=ones(F, length(graphs))) where {F,W}
```

Given a vector 𝐠 of graphs and an equally-sized vector 𝐜 of constants, returns a new graph representing the linear combination (𝐜 ⋅ 𝐠).  The function identifies unique graphs from the input `graphs` and sums their associated `constants`. All input graphs must have the same orders.

# Arguments:

  * `graphs`  vector of computational graphs
  * `constants`  vector of scalar multiples (defaults to ones(F, length(graphs))).

# Returns:

  * A new `Graph{F,W}` object representing the linear combination of the unique input `graphs` weighted by the constants,

where duplicate graphs in the input `graphs` are combined by summing their associated constants. 

# Example:

```
Given graphs `g1`, `g2`, `g1` and constants `c1`, `c2`, `c3`, the function computes `(c1+c3)*g1 + c2*g2`.
```
