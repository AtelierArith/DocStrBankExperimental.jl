Uses the Clenshaw-Curtis method to numerically integrates a function, `f`, over all dimensions except `pos` by approximating the function with a Smolyak polynomial according to the approximation `plan`.  Returns a function.

# Signature

integral = smolyak*clenshaw*curtis(f,plan,pos)

# Example

```
julia> f(x) = sum(x.^2)
julia> splan = smolyak_plan(chebyshev_extrema,4,8,[ones(1,4); zeros(1,4)])
julia> integral = smolyak_clenshaw_curtis(f,splan,4)
julia> integral(0.5)
1.2499999999999996
```
