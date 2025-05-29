```
squad∂squad∂t(qᵢ, A, B, qᵢ₊₁, ta, tb, t)
```

Compute the value and time-derivative of [`squad`](@ref).

This is primarily an internal helper function, taking various parameters computed within the `squad` function.  This will be used to compute the derivative of `squad` when the angular velocity is also requested.  To actually obtain the derivative, simply pass the relevant keyword to the `squad` function.
