```
edit_distance(G₁::AbstractGraph, G₂::AbstractGraph)
```

Compute the edit distance between graphs `G₁` and `G₂`. Return the minimum edit cost and edit path to transform graph `G₁` into graph `G₂``. An edit path consists of a sequence of pairs of vertices``(u,v) ∈ [0,|G₁|] × [0,|G₂|]`` representing vertex operations:

  * $(0,v)$: insertion of vertex $v ∈ G₂$
  * $(u,0)$: deletion of vertex $u ∈ G₁$
  * $(u>0,v>0)$: substitution of vertex $u ∈ G₁$ by vertex $v ∈ G₂$

### Optional Arguments

  * `vertex_insert_cost::Function=v->0.`
  * `vertex_delete_cost::Function=u->0.`
  * `vertex_subst_cost::Function=(u, v)->0.`
  * `edge_insert_cost::Function=e->1.`
  * `edge_delete_cost::Function=e->1.`
  * `edge_subst_cost::Function=(e1, e2)->0.`

The algorithm will always try to match two edges if it can, so if it is preferrable to delete two edges rather than match these, it should be reflected in the `edge_subst_cost` function.

By default, the algorithm uses constant operation costs. The user can provide classical Minkowski costs computed from vertex labels μ₁ (for G₁) and μ₂ (for G₂) in order to further guide the search, for example:

```
edit_distance(G₁, G₂, subst_cost=MinkowskiCost(μ₁, μ₂))
```

  * `heuristic::Function=DefaultEditHeuristic`: a custom heuristic provided to the A*

search in case the default heuristic is not satisfactory.

### Performance

  * Given two graphs $|G₁| < |G₂|$, `edit_distance(G₁, G₂)` is faster to

compute than `edit_distance(G₂, G₁)`. Consider swapping the arguments if involved costs are equivalent.

  * The use of a heuristic can improve performance considerably.
  * Exploit vertex attributes when designing operation costs.

### References

  * RIESEN, K., 2015. Structural Pattern Recognition with Graph Edit Distance: Approximation Algorithms and Applications. (Chapter 2)

### Author

  * Júlio Hoffimann Mendes (juliohm@stanford.edu)

# Examples

```jldoctest
julia> using Graphs

julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> edit_distance(g1, g2)
(3.0, Tuple[(1, 3), (2, 1), (3, 2), (4, 0), (5, 0)])
```
