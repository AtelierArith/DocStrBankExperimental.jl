```
ExplicitNewmark(M::Union{SparseTensor, SparseMatrixCSC}, Z1::Union{Missing, SparseTensor, SparseMatrixCSC}, Z2::Union{Missing, SparseTensor, SparseMatrixCSC}, Δt::Float64)
```

An explicit Newmark integrator for 

$$
M \ddot{\mathbf{d}} + Z_1 \dot{\mathbf{d}} + Z_2 \mathbf{d} + f = 0
$$

The numerical scheme is 

$$
\left(\frac{1}{\Delta t^2} M + \frac{1}{2\Delta t}Z_1\right)d^{n+1} = \left(\frac{2}{\Delta t^2} M - \frac{1}{2\Delta t}Z_2\right)d^n - \left(\frac{1}{\Delta t^2} M - \frac{1}{2\Delta t}Z_1\right) d^{n-1} - f
$$

To use this integrator, 

```julia
en = ExplicitNewmark(M, Z1, Z2, Δt)
d2 = step(en, d0, d1, f)
```
