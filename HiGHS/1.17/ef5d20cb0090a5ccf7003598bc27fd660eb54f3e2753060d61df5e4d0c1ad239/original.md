```
Highs_destroy(highs)
```

Destroy the model `highs` created by [`Highs_create`](@ref) and free all corresponding memory. Future calls using `highs` are not allowed.

To empty a model without invalidating `highs`, see [`Highs_clearModel`](@ref).

### Parameters

  * `highs`: A pointer to the Highs instance.
