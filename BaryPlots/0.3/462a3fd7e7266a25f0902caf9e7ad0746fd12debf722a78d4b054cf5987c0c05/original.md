```
ternary_coords(x::Vector{Float64}) -> Tuple{Float64, Float64}
```

Converts a vector `x` of three strategy frequencies `[x₁, x₂, x₃]` into ternary coordinates `(X, Y)` for plotting within a simplex (equilateral triangle).

# Arguments

  * `x`: A vector of length 3, representing the frequencies of three strategies. The frequencies can sum to any positive value; they will be normalized within the function.

# Returns

  * A tuple `(X, Y)` representing the ternary coordinates of the input vector.

# Notes

  * This function ensures that the sum of the frequencies equals 1 by normalizing `x`.
  * The ternary coordinates are calculated based on the normalized frequencies for plotting in a 2D simplex.
