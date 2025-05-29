```
place_knvd(A::AbstractMatrix, B, λ; verbose = false, init = :s)
```

Robust pole placement using the algorithm from

> "Robust Pole Assignment in Linear State Feedback", Kautsky, Nichols, Van Dooren


This implementation uses "method 0" for the X-step and the QR factorization for all factorizations.

This function will be called automatically when [`place`](@ref) is called with a MIMO system.

# Arguments:

  * `init`: Determines the initialization strategy for the iterations for find the `X` matrix. Possible choices are `:id` (default), `:rand`, `:s`.
