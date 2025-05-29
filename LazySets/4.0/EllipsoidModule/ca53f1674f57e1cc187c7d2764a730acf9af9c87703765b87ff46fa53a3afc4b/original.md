# Extended help

```
rand(::Type{Ellipsoid}; [N]::Type{<:AbstractFloat}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

The center is a normally distributed vector with entries of mean 0 and standard deviation 1.

The idea for the shape matrix comes from [here](https://math.stackexchange.com/a/358092). The matrix is symmetric positive definite, but also diagonally dominant.

$$
Q =  \frac{1}{2}(S + S^T) + nI,
$$

where $n$ = `dim` and $S$ is a $n × n$ random matrix whose coefficients are uniformly distributed in the interval $[-1, 1]$.
