```
pcl_hessian(y::PyObject, x::PyObject)
```

Returns the Hessian tensor for the operator 

$$
y = F(x)
$$

$$
x\in \mathbb{R}^m
$$

and $y\in \mathbb{R}^n$ are 1D vectors. The function returns a tuple 

  * `H`: $m\times m$ Hessian matrix
  * `W`: $n\times n$ Hessian matrix from downstream of the computational graph
  * `dy`: length $n$ tensor; gradient from downstream of the computational graph
