```julia
DiffEqArray(u::AbstractVector, t::AbstractVector)
```

This is a `VectorOfArray`, which stores `A.t` that matches `A.u`. This will plot `(A.t[i],A[i,:])`. The function `tuples(diffeq_arr)` returns tuples of `(t,u)`.

To construct a DiffEqArray

```julia
t = 0.0:0.1:10.0
f(t) = t - 1
f2(t) = t^2
vals = [[f(tval) f2(tval)] for tval in t]
A = DiffEqArray(vals, t)
A[1, :]  # all time periods for f(t)
A.t
```
