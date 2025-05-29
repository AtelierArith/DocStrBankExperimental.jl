```
sum_kahan(v::AbstractVector{T}) where {T<:Number}
```

Neumaier's variant of Kahan summation algorithm to reduce numerical errors.

# Note

  * Slower than `sum_xsum` for large vectors, but faster for small vectors.
  * Uses loop unrolling for better performance while maintaining Kahan summation's

numerical stability. Processes two elements per iteration when possible.

# References

  * [JuliaMath/KahanSummation.jl](https://github.com/JuliaMath/KahanSummation.jl)
