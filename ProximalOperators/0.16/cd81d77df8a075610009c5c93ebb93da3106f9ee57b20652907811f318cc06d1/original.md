```
IndPSD(;scaling=false)
```

Return the indicator of the positive semi-definite cone

$$
C = \{ X : X \succeq 0 \}.
$$

The argument to the function can be either a `Symmetric`, `Hermitian`, or `AbstractMatrix` object, or an object of type `AbstractVector{Float64}` holding a symmetric matrix in (lower triangular) packed storage.

If `scaling = true` then the vectors `y` and `x` in `prox!(y::AbstractVector{Float64}, f::IndPSD, x::AbstractVector{Float64}, args...)` have the off-diagonal elements multiplied with `√2` to preserve inner products, see Vandenberghe 2010: http://www.seas.ucla.edu/~vandenbe/publications/coneprog.pdf .

I.e. when when `scaling=true`, let `X,Y` be matrices and

`x = (X_{1,1}, √2⋅X_{2,1}, ... ,√2⋅X_{n,1}, X_{2,2}, √2⋅X_{3,2}, ..., X_{n,n})`,

`y = (Y_{1,1}, √2⋅Y_{2,1}, ... ,√2⋅Y_{n,1}, Y_{2,2}, √2⋅Y_{3,2}, ..., Y_{n,n})`

then `prox!(Y, f, X)` is equivalent to `prox!(y, f, x)`.
