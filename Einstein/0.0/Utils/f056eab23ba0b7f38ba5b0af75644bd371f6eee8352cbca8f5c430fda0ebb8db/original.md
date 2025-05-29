```
sum_xsum(vec::AbstractVector{Float64})
```

Compute the sum of a vector using extended precision accumulation. Uses the `xsum` package for improved numerical accuracy.

# Note

  * Very fast for large vectors, but a bit slower than Kahan summation for small vectors (n ⪅ 80)

# References

  * [neal2015fastexactsummationusing](@citet*)
  * [JuliaMath/Xsum.jl](https://github.com/JuliaMath/Xsum.jl)
  * [Radford Neal / xsum · GitLab](https://gitlab.com/radfordneal/xsum)
