Numerically integrates a function, `f`, over all dimensions by approximating the function with a Smolyak polynomial according to the approximation `plan`, using either :clenshaw*curtis or gauss*Chebyshev_quad  as `method`.  Returns a scalar.

# Signature

integral = smolyak_integrate(f,plan,method)

# Example

```
julia> f(x) = sum(x.^2)
julia> splan = smolyak_plan(chebyshev_extrema,4,8,[ones(1,4); zeros(1,4)])
julia> integral = smolyak_integrate(f,splan,:clenshaw_curtis)
1.3333333333333328
julia> integral = smolyak_integrate(f,splan,:gauss_chebyshev_quad)
1.3318637929187602
```
