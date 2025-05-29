```
TR_BDF2(D0::Union{SparseTensor, SparseMatrixCSC}, 
    D1::Union{SparseTensor, SparseMatrixCSC}, 
    Δt::Float64)
```

Constructs a TR-BDF2 (the Trapezoidal Rule with Second Order Backward Difference Formula) handler for  the DAE 

$$
D_1 \dot y + D_0 y = f
$$

The struct is a functor, which performs one step simulation 

```
(tr::TR_BDF2)(y::Union{PyObject, Array{Float64, 1}}, 
    f1::Union{PyObject, Array{Float64, 1}}, 
    f2::Union{PyObject, Array{Float64, 1}}, 
    f3::Union{PyObject, Array{Float64, 1}})
```

Here `f1`, `f2`, and `f3` correspond to the right hand side at time step $n$, $n+\frac12$, and $n+1$.

Or we can pass a batched `F` defined as a `(2NT+1) × DOF` array

```
(tr::TR_BDF2)(y0::Union{PyObject, Array{Float64, 1}}, 
    F::Union{PyObject, Array{Float64, 2}})
```

The output will be the entire solution of size `(NT+1) × DOF`.

!!! info
    The scheme takes the following form for n = 0, 1, ... $\begin{aligned} D_1(y^{n+\frac12}-y^n) = \frac12\frac{\Delta t}{2}\left(f^{n+\frac12} + f^n - D_0 \left(y^{n+\frac12} + y^n\right)\right)\\ \left(\frac{\Delta t}{2}\right)^{-1} D_1 \left(\frac32y^{n+1} - 2y^{n+\frac12} + \frac12 y^n\right) + D_0 y^{n+1} = f^{n+1}\end{aligned}$

