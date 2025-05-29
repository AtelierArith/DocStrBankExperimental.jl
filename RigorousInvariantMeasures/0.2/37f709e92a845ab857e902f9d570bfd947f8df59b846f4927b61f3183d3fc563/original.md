Compute the guaranteed interval preimage f⁻¹(y) of a point y ∈ R according to the function f: [a,b] → R.  This preimage is guaranteed to lie inside the real interval `x = hull(a,b)`.

`f` must be strictly monotonic on [a,b], at least in the sense of MonotonicBranch functions (allowing for uncertainty on the endpoints). `f` must be differentiable; zero and infinite derivative are allowed.

`y1`, `y2` must be guaranteed to be equal to f(a), f(b) or "more outside", so that  y ∉ hull(y1,f(z)) ⟹ f⁻¹(y) ∉ hull(a, z).

Stops when the interval reaches a fixed point, when the diameter is smaller than ε, or when max_iter iterations are reached (with an error)
