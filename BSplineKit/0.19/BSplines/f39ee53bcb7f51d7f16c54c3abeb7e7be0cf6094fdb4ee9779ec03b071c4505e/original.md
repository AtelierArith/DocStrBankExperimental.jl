```
PeriodicKnots{T} <: AbstractVector{T}
```

Describes an infinite vector of knots with periodicity `L`.

---

```
PeriodicKnots(ξs::AbstractVector{T}, ::BSplineOrder{k})
```

Construct a periodic knot sequence from breakpoints `ξs`.

The knot period is taken to be `L = ξs[end] - ξs[begin]`. In other words, the breakpoints `ξs` are expected to include the endpoint `ξs[begin] + L`.

The breakpoints should be given in non-decreasing order.

Note that the indices of the returned knots `ts` are offset with respect to the input `ξs` according to `ts[i] = ξs[i + offset]` where `offset = k ÷ 2`.
