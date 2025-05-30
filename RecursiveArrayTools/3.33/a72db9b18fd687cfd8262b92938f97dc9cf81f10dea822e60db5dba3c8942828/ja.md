```julia
DiffEqArray(u::AbstractVector, t::AbstractVector)
```

これは `VectorOfArray` であり、`A.u` に一致する `A.t` を格納します。これは `(A.t[i],A[i,:])` をプロットします。関数 `tuples(diffeq_arr)` は `(t,u)` のタプルを返します。

DiffEqArray を構築するには

```julia
t = 0.0:0.1:10.0
f(t) = t - 1
f2(t) = t^2
vals = [[f(tval) f2(tval)] for tval in t]
A = DiffEqArray(vals, t)
A[1, :]  # f(t) のすべての時間期間
A.t
```
