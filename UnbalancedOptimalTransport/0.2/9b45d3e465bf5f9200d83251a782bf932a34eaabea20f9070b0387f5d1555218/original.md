```
DiscreteMeasure(density, [log_density], set) -> DiscreteMeasure
```

Construct a `DiscreteMeasure` object for use in [`unbalanced_sinkhorn!`](@ref) and related functions.

  * `density` should be strictly positive; zero elements should instead be removed from `set`
  * `log_density` should be equal to `log.(density)` and can be omitted (in which case its computed automatically)
  * `set` is a collection so that `density[i]` is the probability of the element `set[i]` occurring (where `i ∈ eachindex(density, set)`).
