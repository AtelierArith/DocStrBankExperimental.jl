```
@compound
```

Macro that creates a compound species, which is composed of smaller component species.

Example:

```julia
t = default_t()
@species C(t) O(t)
@compound CO2(t) ~ C + 2O
```

Notes:

  * The component species must be defined before using the `@compound` macro.
