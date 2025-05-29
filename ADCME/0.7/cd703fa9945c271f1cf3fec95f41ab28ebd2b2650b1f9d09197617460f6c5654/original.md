```
hessian(ys::PyObject, xs::PyObject; kwargs...)
```

`hessian` computes the hessian of a scalar function f with respect to vector inputs xs. 

# Example

```julia
x = constant(rand(10))
y = 0.5 * sum(x^2)
o = hessian(y, x)

sess = Session(); init(sess)
run(sess, o) # should be an identity matrix
```
