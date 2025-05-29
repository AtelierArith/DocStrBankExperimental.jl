```
dot_xsum(x::StridedVector{T}, y::StridedVector{T}) where {T<:Real}
```

Compute the dot product of two vectors using extended precision accumulation. Uses the `xsum` package for improved numerical accuracy.

# Note

  * Very fast for large vectors, but a bit slower than Kahan summation for small vectors.
  * Both input vectors must have the same length, which is not checked for performance reasons.

# References

  * [neal2015fastexactsummationusing](@citet*)
  * [JuliaMath/Xsum.jl](https://github.com/JuliaMath/Xsum.jl)
  * [Radford Neal / xsum · GitLab](https://gitlab.com/radfordneal/xsum)
