```
flipgraph_modular(D::DeltaComplex; kwargs..)
```

Construct the **modular flip graph** for the closed orientable surface defined by the *Δ-complex* `D`.  

# Arguments

  * `labeled_points :: Bool = true` : If is set to `false`, then the isomorphism also includes a renaming of the points.
  * `depth :: Integer = ∞` : Determines the depth to which the flip graph should be constructed. i.e. up to which distance from `D`.
