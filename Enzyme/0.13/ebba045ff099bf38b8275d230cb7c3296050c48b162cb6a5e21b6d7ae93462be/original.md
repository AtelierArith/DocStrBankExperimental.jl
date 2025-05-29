```
jacobian(::ReverseMode, f, x; n_outs=nothing, chunk=nothing)
jacobian(::ReverseMode, f, x)
```

Compute the jacobian of a array-output function `f` using (potentially vector) reverse mode. The `chunk` argument optionally denotes the chunk size to use and `n_outs` optionally denotes the shape of the array returned by `f` (e.g `size(f(x))`).

Example:

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

jacobian(Reverse, f, [2.0, 3.0, 4.0])

# output
([3.0 2.0 0.0; 0.0 1.0 1.0],)
```

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = jacobian(ReverseWithPrimal, f, [2.0, 3.0, 4.0])

# output
(derivs = ([3.0 2.0 0.0; 0.0 1.0 1.0],), val = [6.0, 7.0])
```

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = jacobian(Reverse, f, [2.0, 3.0, 4.0], n_outs=Val((2,)))

# output
([3.0 2.0 0.0; 0.0 1.0 1.0],)
```

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = jacobian(ReverseWithPrimal, f, [2.0, 3.0, 4.0], n_outs=Val((2,)))

# output
(derivs = ([3.0 2.0 0.0; 0.0 1.0 1.0],), val = [6.0, 7.0])
```

This function will return an AbstractArray whose shape is `(size(output)..., size(input)...)`. No guarantees are presently made about the type of the AbstractArray returned by this function (which may or may not be the same as the input AbstractArray if provided).

In the future, when this function is extended to handle non-array return types,  this function will retun an AbstractArray of shape `size(output)` of values of the input type.  ```
