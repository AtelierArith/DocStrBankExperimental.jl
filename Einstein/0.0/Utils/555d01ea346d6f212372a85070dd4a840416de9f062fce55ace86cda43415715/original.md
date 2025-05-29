```
dot_kahan(v1::StridedVector{T}, v2::StridedVector{T}) where {T<:Number}
```

Neumaier's variant of Kahan summation algorithm to reduce numerical errors.

# Note

  * Slower than `dot_xsum` for large vectors, but faster for small vectors.
  * Similar performance to `dot_kahan`
  * Uses loop unrolling for better performance while maintaining Kahan summation's

numerical stability. Processes two elements per iteration when possible.

# References

  * [JuliaMath/KahanSummation.jl](https://github.com/JuliaMath/KahanSummation.jl)
