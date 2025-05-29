```
function linear_combination(graphs::Vector{FeynmanGraph{F,W}}, constants::AbstractVector=ones(F, length(graphs))) where {F,W}
```

Given a vector 𝐠 of graphs each with the same type and external/internal vertices and  an equally-sized vector 𝐜 of constants, returns a new graph representing the linear combination (𝐜 ⋅ 𝐠).  The function identifies unique graphs from the input `graphs` and sums their associated `constants`. All input Graphs must have the same diagram type, orders, and external vertices.

# Arguments:

  * `graphs`  vector of input FeymanGraphs
  * `constants`  vector of scalar multiples (defaults to ones(F, length(graphs))).

# Returns:

  * A new `FeynmanGraph{F,W}` object representing the linear combination of the unique input `graphs` weighted by the constants,

where duplicate graphs in the input `graphs` are combined by summing their associated constants. 

# Example:

```
Given graphs `g1`, `g2`, `g1` and constants `c1`, `c2`, `c3`, the function computes `(c1+c3)*g1 + c2*g2`.
```
