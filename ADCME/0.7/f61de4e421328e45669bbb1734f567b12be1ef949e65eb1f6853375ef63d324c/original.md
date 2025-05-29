```
svd(o::PyObject, args...; kwargs...)
```

Returns a `TFSVD` structure which holds the following data structures

```julia
S::PyObject
U::PyObject
V::PyObject
Vt::PyObject
```

We have the equality $o = USV'$

# Example

```julia
A = rand(10,20)
r = svd(constant(A))
A2 = r.U*diagm(r.S)*r.Vt # The value of `A2` should be equal to `A`
```
