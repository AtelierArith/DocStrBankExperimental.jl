```
flatmap(f, X)
```

Apply `f` to all elements of `X` and flatten the result by concatenating all `f(x)` collections. Similar to `mapreduce(f, vcat, X)`, more efficient and generic.

```
flatmap(fₒᵤₜ, fᵢₙ, X)
```

Apply `fₒᵤₜ` to all elements of `X`, and apply `fᵢₙ` to the results. Basically, `[fᵢₙ(x, y) for x in X for y in fₒᵤₜ(x)]`.
