```julia
treeProductUp(fg, tree, cliq, sym; N, dbg)

```

Calculate a fresh (single step) approximation to the variable `sym` in clique `cliq` as though during the upward message passing.  The full inference algorithm may repeatedly calculate successive apprimxations to the variables based on the structure of the clique, factors, and incoming messages. Which clique to be used is defined by frontal variable symbols (`cliq` in this case) – see `getClique(...)` for more details.  The `sym` symbol indicates which symbol of this clique to be calculated.  **Note** that the `sym` variable must appear in the clique where `cliq` is a frontal variable.
