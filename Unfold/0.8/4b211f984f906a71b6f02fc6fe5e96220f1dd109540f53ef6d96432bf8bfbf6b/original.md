```
effects(design::AbstractDict, model::UnfoldModel; typical = mean)
```

Calculates marginal effects for all term combinations in `design`.

Implementation based on Effects.jl package; likely could repackage in UnfoldEffects.jl; somebody wants to do it? This would make it easier to cross-maintain it to changes/bug fixes in the Effects.jl package. `design` is a dictionary containing those predictors (as keys) with levels (as values), that you want to evaluate. The `typical` refers to the value, which other predictors that are not specified in the dictionary, should take on.

For MixedModels, the returned effects are based on the "typical" subject, i.e. all random effects are put to 0.

# Example

```julia-repl
 julia> f = @formula 0 ~ categoricalA + continuousA + continuousB
 julia> uf = fit(UnfoldModel, (Any => (f, times)), data, events)
 julia> d = Dict(:categorical => ["levelA", "levelB"], :continuous => [-2, 0, 2])
 julia> effects(d, uf)
```

will result in 6 predicted values: A/-2, A/0, A/2, B/-2, B/0, B/2.
