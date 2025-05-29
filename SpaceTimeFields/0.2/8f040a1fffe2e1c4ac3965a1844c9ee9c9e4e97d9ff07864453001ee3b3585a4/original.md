```
Gaussian(σ,A)
```

Construct a 1-d Gaussian function with standard deviation `σ` and amplitude `A`.  The resulting function can be evaluated at any real-valued number.

# Example

```jldoctest
julia> g = Gaussian(0.2,1)
Gaussian(0.2, 1, 2.8209479177387813)

julia> g(0.2)
1.0377687435514866
```
