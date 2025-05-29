```
SimpleChain([inputdim::Union{Integer,Tuple{Vararg{Integer}}, ] layers)
```

Construct a SimpleChain. Optional `inputdim` argument allows `SimpleChains` to check the size of inputs. Making these `static` will allow `SimpleChains` to infer size and loop bounds at compile time. Batch size generally should not be included in the `inputdim`. If `inputdim` is not specified, some methods, e.g. `init_params`, will require passing the size as an additional argument, because the number of parameters may be a function of the input size (e.g., for a `TurboDense` layer).

The `layers` argument holds various `SimpleChains` layers, e.g. `TurboDense`, `Conv`, `Activation`, `Flatten`, `Dropout`, or `MaxPool`. It may optionally terminate in an `AbstractLoss` layer.

These objects are callable, e.g.

```julia
c = SimpleChain(...);
p = SimpleChains.init_params(c);
c(X, p) # X are the independent variables, and `p` the parameter vector.
```
