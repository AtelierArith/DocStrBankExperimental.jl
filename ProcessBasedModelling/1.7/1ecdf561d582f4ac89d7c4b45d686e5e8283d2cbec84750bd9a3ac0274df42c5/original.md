```
new_derived_named_parameter(variable, value, extra::String; kw...)
```

If `value isa Num` return `value`. If `value isa LiteralParameter`, replace it with its literal value. Otherwise, create a new MTK `@parameter` whose name is created from `variable` (which could also be just a `Symbol`) by adding the `extra` string.

**Keywords**:

  * `prefix = true`: whether the `extra` is added at the start or the end, connecting with the with the `connector`.
  * `connector = "_"`: what to use to connect `extra` with the name.

For example,

```
@variables x(t)
p = new_derived_named_parameter(x, 0.5, "τ")
```

Now `p` will be a parameter with name `:τ_x` and default value `0.5`.
