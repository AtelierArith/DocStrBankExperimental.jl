```julia
plotUpMsgsAtCliq(treel, cllb, lb; show, w, h, levels, dims)

```

Draw the upward belief from clique `cllb::Symbol` message on variable `lb::Symbol`.

Example:

```julia
plotUpMsgsAtCliq(tree, :x2, :x1)
```

Related

plotKDE, getUpMsgs
