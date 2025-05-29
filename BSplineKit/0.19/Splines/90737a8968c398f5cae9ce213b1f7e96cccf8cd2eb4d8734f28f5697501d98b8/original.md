```
Spline{T} <: Function
```

Represents a spline function.

---

```
Spline(B::AbstractBSplineBasis, coefs::AbstractVector)
```

Construct a spline from a B-spline basis and a vector of B-spline coefficients.

# Examples

```jldoctest; filter = r"coefficients: \[.*\]"
julia> B = BSplineBasis(BSplineOrder(4), -1:0.2:1);

julia> coefs = rand(length(B));

julia> S = Spline(B, coefs)
13-element Spline{Float64}:
 basis: 13-element BSplineBasis of order 4, domain [-1.0, 1.0]
 order: 4
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 coefficients: [0.173575, 0.321662, 0.258585, 0.166439, 0.527015, 0.483022, 0.390663, 0.802763, 0.721983, 0.372347, 0.0301856, 0.0793339, 0.663758]
```

---

```
Spline{T = Float64}(undef, B::AbstractBSplineBasis)
```

Construct a spline with uninitialised vector of coefficients.

---

```
(S::Spline)(x)
```

Evaluate spline at coordinate `x`.
