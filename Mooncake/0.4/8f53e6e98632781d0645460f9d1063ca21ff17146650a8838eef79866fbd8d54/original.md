```
value_and_gradient!!(rule, f, x...)
```

Equivalent to `value_and_pullback!!(rule, 1.0, f, x...)`, and assumes `f` returns a `Union{Float16,Float32,Float64}`.

*Note:* There are lots of subtle ways to mis-use `value_and_pullback!!`, so we generally recommend using `Mooncake.value_and_gradient!!` (this function) where possible. The docstring for `value_and_pullback!!` is useful for understanding this function though.

An example:

```jldoctest
f(x, y) = sum(x .* y)
x = [2.0, 2.0]
y = [1.0, 1.0]
rule = build_rrule(f, x, y)
value_and_gradient!!(rule, f, x, y)

# output

(4.0, (NoTangent(), [1.0, 1.0], [2.0, 2.0]))
```
