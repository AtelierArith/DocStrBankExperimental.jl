```
WrappedFunction(f)
```

Wraps a stateless and parameter less function. Might be used when a function is added to `Chain`. For example, `Chain(x -> relu.(x))` would not work and the right thing to do would be `Chain((x, ps, st) -> (relu.(x), st))`. An easier thing to do would be `Chain(WrappedFunction(Base.Fix1(broadcast, relu)))`

## Arguments

  * `f`: Some function.

## Inputs

  * `x`: will be directly passed to `f`

## Returns

  * Output of `f(x)`
  * Empty `NamedTuple()`
