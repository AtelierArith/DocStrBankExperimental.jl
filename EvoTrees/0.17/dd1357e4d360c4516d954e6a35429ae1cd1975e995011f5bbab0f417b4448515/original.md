```
EvoTree{L,K}
```

An `EvoTree` holds the structure of a fitted gradient-boosted tree.

# Fields

  * trees::Vector{Tree{L,K}}
  * info::Dict

`EvoTree` acts as a functor to perform inference on input data: 

```
pred = (m::EvoTree; ntree_limit=length(m.trees))(x)
```
