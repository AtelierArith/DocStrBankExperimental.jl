```
@compounds
```

Macro that creates several compound species, which each is composed of smaller component species. Uses the same syntax as `@compound`, but with one compound species one each line.

Example:

```julia
t = default_t()
@species C(t) H(t) O(t)
@compounds
    CH4(t) = C + 4H
    O2(t) = 2O
    CO2(t) = C + 2O
    H2O(t) = 2H + O
end
```

Notes:

  * The component species must be defined before using the `@compound` macro.
