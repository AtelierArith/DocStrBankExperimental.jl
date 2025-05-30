```
value_and_pullback!!(rule, ȳ, f, x...)
```

Compute the value and pullback of `f(x...)`. `ȳ` must be a valid tangent for the primal return by `f(x...)`.

`rule` should be constructed using `build_rrule`.

*Note:* There are lots of subtle ways to mis-use `value_and_pullback!!`, so we generally recommend using `value_and_gradient!!` where possible.

*Note:* If calling `value_and_pullback!!` multiple times for various values of `x`, you should use the same instance of `rule` each time.

*Note:* It is your responsibility to ensure that there is no aliasing in `f` and `x`. For example,

```julia
X = randn(5, 5)
rule = build_rrule(dot, X, X)
value_and_pullback!!(rule, 1.0, dot, X, X)
```

will yield the wrong result.

*Note:* This method of `value_and_pullback!!` has to first call `zero_codual` on all of its arguments. This may cause some additional allocations. If this is a problem in your use-case, consider pre-allocating the `CoDual`s and calling the other method of this function. The `CoDual`s should be primal-tangent pairs (as opposed to primal-fdata pairs). There are lots of ways to get this wrong though, so we generally advise against doing this.
