Macro to add simplification rules. Example:

```
@simple_rule (-x * -y) (x * y)
```

where `(-x * -y)` is a pattern to match expression and `(x * y)` is what it should be transformed to (see `rewrite()` to understand expression rewriting). Symbols Set([:a, :b, :y, :x]) may be used as placeholders when defining new rules, all other symbols will be taken literally.
