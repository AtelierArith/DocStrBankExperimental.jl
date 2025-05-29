```
Grid <: ParameterSource

Grid{K}()
Grid(K::Symbol)
```

Use grid with key `K` as a parameter source.

Implemented in rules with:

```julia
get(data, rule.myparam, I)
```

And specified at rule construction with:

```julia
SomeRule(; myparam=Grid(:somegrid))
```
