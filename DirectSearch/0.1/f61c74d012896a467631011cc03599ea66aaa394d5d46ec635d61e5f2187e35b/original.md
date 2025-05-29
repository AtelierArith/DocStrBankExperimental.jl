```
AddProgressiveCollection(p::Constraints{FT}; h_max=Inf, h_max_update::Function=h_max_update,
                         aggregator::Function=x->max(0,x)^2)::CollectionIndex where {FT<:AbstractFloat}
```

Instantiate a new constraint collection within the problem. Returns an index that refers to this new collection.

The default constraint settings match those from Audet & Dennis 2009:

`h_max`: Begins as infinity

`h_max_update`: Sets h_max to the largest valid h evaluation if an iteration is improving

`aggregator`: Creates h as $\sum k(x)$ where $k=\max(0,x)^2$
