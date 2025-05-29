```
ApproxByInterpolation <: AbstractApproxMethod
```

Approximate function by a spline that passes through the given set of points.

The number of points must be equal to the length of the B-spline basis defining the approximation space.

See belows for different ways of specifying the interpolation points.

---

```
ApproxByInterpolation(xs::AbstractVector)
```

Specifies an approximation by interpolation at the given points `xs`.

---

```
ApproxByInterpolation(B::AbstractBSplineBasis)
```

Specifies an approximation by interpolation at an automatically-determined set of points, which are expected to be appropriate for the given basis.

The interpolation points are determined by calling [`collocation_points`](@ref).
