Uses the Clenshaw-Curtis method to numerically integrates a function, `f`, over all dimensions by approximating the function with a Smolyak polynomial according to the approximation `plan`.  Returns a scalar.

# Signature

integral = smolyak*clenshaw*curtis(f,plan)

# Example

```
julia> f(x) = sum(x.^2)
julia> splan = smolyak_plan(chebyshev_extrema,4,8,[ones(1,4); zeros(1,4)])
julia> integral = smolyak_clenshaw_curtis(f,splan)
1.3333333333333328
```
