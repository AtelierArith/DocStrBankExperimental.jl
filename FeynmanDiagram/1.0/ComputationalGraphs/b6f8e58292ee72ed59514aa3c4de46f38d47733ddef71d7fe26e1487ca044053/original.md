```
function flatten_chains!(g::AbstractGraph)

Recursively flattens chains of subgraphs within the given graph `g` by merging certain trivial unary subgraphs 
into their parent graphs in the in-place form.

Acts only on subgraphs of `g` with the following structure: 𝓞 --- 𝓞' --- ⋯ --- 𝓞'' ⋯ (!),
where the stop-case (!) represents a leaf, a non-trivial unary operator 𝓞'''(g) != g, or a non-unary operation.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
