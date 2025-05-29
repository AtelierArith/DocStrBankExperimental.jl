```
embed_graph([mode,] g::SimpleGraph; vertex_order=MinhThiTrick())
```

Embed graph `g` into a unit disk grid, where the optional argument `mode` can be `Weighted()` or `UnWeighted`. The `vertex_order` can be a vector or one of the following inputs

```
* `Greedy()` fast but non-optimal.
* `MinhThiTrick()` slow but optimal.
```
