```
valgrad!(g, c::SimpleChain, arg, params)
```

`g` can be either an `AbstractVector` with the same size as `params`, or a `Tuple{A,G}`. If `g` is a tuple, the first element is the gradient with respect to `arg`, and should either be `nothing` (for not taking this gradient) or have the same `size` as arg. The second element is the gradient with respect to `params`, and should likewise either be `nothing` or have the same size as `params`.

Allowed destruction:

```
valgrad_layer!
```

Accepts return of previous layer (`B`) and returns an ouput `C`. If an internal layer, allowed to destroy `B` (e.g. dropout layer).

```
pullback!
```

Accepts adjoint of its return (`C̄`). It is allowed to destroy this. It is also allowed to destroy the previous layer's return `B` to produce `B̄` (the `C̄` it receives). Thus, the pullback is not allowed to depend on `C`, as it may have been destroyed in producing `C̄`.
