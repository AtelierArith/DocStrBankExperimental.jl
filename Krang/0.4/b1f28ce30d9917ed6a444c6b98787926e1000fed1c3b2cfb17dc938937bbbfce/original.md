```
Kerr(spin::T) where {T}
```

Constructs a `Kerr` object representing the Kerr metric.

# Arguments

  * `spin::T`: The spin parameter `a = J/M`, where `J` is the angular momentum and `M` is the mass of the black hole. spin ∈ (-1, 0) ∪ (0, 1).

# Returns

  * A `Kerr` object with the given spin and a default mass of 1.
