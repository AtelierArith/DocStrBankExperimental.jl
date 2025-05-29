```
gen(P, X0, model, steps; tracker=Returns(nothing), midpoint = false)
```

Constructs a sequence of (stochastic) bridges between `X0` and the predicted `X̂₁` under the process `P`. `P`, `X0`, can also be tuples where the Nth element of `P` will be used for the Nth elements of `X0` and `model`. model is a function that takes `t` (scalar) and `Xₜ` (optionally a tuple) and returns `hat` (a `UState`, a flat tensor with the right shape, or a tuple of either if you're combining processes). If `X0` is a `MaskedState`, then anything in `X̂₁` will be conditioned on `X0` where the conditioning mask `X0.cmask` is 1.
