```
QuadLimbDark(u::AbstractVector)
```

A specialized implementation of [`PolynomialLimbDark`](@ref) with a maximum of two terms (quadratic form). This has a completely closed-form solution without any numerical integration. This means there are no intermediate allocations and reduced numerical error.

# Mathematical form

$$
I(\mu) \propto 1 - u_1(1-\mu) - u_2(1-\mu)^2
$$

!!! warning "Higher-order terms"
    Higher-order terms will be *ignored*; no error will be thrown


# Examples

```jldoctest quad
ld = QuadLimbDark(Float64[]) # constant term only

b = [0, 1, 2] # impact parameter
r = 0.01 # radius ratio
ld.(b, r)

# output
3-element Vector{Float64}:
 0.9999
 0.9999501061035608
 1.0
```

```jldoctest quad
ld = QuadLimbDark([0.4, 0.26]) # max two terms
ld.(b, r)

# output
3-element Vector{Float64}:
 0.9998785437247428
 0.999974726693709
 1.0
```

# References

See references for [`PolynomialLimbDark`](@ref)
