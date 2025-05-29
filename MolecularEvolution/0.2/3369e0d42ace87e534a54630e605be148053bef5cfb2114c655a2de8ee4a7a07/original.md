# Constructors

```
LazyDown(stores_obs)
LazyDown() = LazyDown(x::FelNode -> true)
```

# Description

Indicate that we want to do a downward pass, e.g. `sample_down!`. The function passed to the constructor takes a `node::FelNode` as input and returns a `Bool` that decides if `node` stores its observations.
