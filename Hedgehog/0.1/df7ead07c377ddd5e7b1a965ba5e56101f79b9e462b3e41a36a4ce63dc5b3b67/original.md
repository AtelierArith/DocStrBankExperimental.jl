```
CarrMadan(α, bound, dynamics; kwargs...)
```

Constructs a `CarrMadan` method with optional integration settings for `quadgk`.

# Arguments

  * `α`: Damping factor.
  * `bound`: Integration bound (positive real number).
  * `dynamics`: The price dynamics (must support `marginal_law`).
  * `kwargs...`: Additional keyword arguments for `quadgk`.
