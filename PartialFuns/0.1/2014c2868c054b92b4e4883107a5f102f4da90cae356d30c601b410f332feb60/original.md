```
    PartialFun(f, args...; kws...)
```

Construct a partially-applied function which calls `f` on the specified arguments. To specify unfilled arguments, use `UnfixedArg(T)` or `UnfixedArgSplat(T)`, where `T` is the type to assert the unfilled argument take. To avoid type assertion, use `UnfixedArg()` or `UnfixedArgSplat()`.

Example:

```
julia> f = PartialFun(+, 1, UnfixedArg())
+(1, _)

julia> f(2)
3
```
