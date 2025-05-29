# Caputo sense fractional derivative.

```
fracdiff(f::Function, α, start_point, end_point, step_size, ::Caputo)
```

### Example:

```julia-repl
julia> fracdiff(x->x^5, 0.5, 0, 2.5, 0.0001, CaputoDirect())
```

Returns a tuple (**result**, **error**), which means the value of this derivative is 141.59714979764541, and the error estimate is 1.1532243848672914e-6.

Refer to [Caputo derivative](https://en.wikipedia.org/wiki/Fractional_calculus#Caputo_fractional_derivative)

!!! note
    `Caputo Direct` algorithms belong to direct computing, precise are ensured, but maybe cause more memory allocation and take more compilation time.


Using the direct mathematic expression:

$$
^CD_t^α=\frac{1}{\Gamma(n-α)}\int_0^t\frac{f^{(n)}(τ)}{(t-τ)^{α+1-n}}
$$

As for the derivative inside the integral, we use the **Complex Step Differentiation** to obtain a more accurate value.
