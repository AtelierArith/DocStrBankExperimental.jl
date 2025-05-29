```
gradient(::ForwardMode, f, x; shadows=onehot(x), chunk=nothing)
```

Compute the gradient of an array-input function `f` using forward mode. The optional keyword argument `shadow` is a vector of one-hot vectors of type `x` which are used to forward-propagate into the return. For performance reasons, this should be computed once, outside the call to `gradient`, rather than within this call.

Example:

```jldoctest gradfwd
f(x) = x[1]*x[2]

gradient(Forward, f, [2.0, 3.0])

# output

([3.0, 2.0],)
```

```jldoctest gradfwd
gradient(ForwardWithPrimal, f, [2.0, 3.0])

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```

```jldoctest gradfwd
gradient(Forward, f, [2.0, 3.0]; chunk=Val(1))

# output

([3.0, 2.0],)
```

```jldoctest gradfwd
gradient(ForwardWithPrimal, f, [2.0, 3.0]; chunk=Val(1))

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```

For functions which return an AbstractArray or scalar, this function will return an AbstractArray whose shape is `(size(output)..., size(input)...)`. No guarantees are presently made about the type of the AbstractArray returned by this function (which may or may not be the same as the input AbstractArray if provided).

For functions who return other types, this function will retun an AbstractArray of shape `size(input)` of values of the output type. 

```jldoctest
f(x) = [ x[1] * x[2], x[2] + x[3] ]

grad = gradient(Forward, f, [2.0, 3.0, 4.0])

# output
([3.0 2.0 0.0; 0.0 1.0 1.0],)
```

This function supports multiple arguments and computes the gradient with respect to each

```jldoctest gradfwd2
mul(x, y) = x[1]*y[2] + x[2]*y[1]

gradient(Forward, mul, [2.0, 3.0], [2.7, 3.1])

# output

([3.1, 2.7], [3.0, 2.0])
```

This includes the ability to mark some arguments as `Const` if its derivative is not needed, returning nothing in the corresponding derivative map.

```jldoctest gradfwd2
gradient(Forward, mul, [2.0, 3.0], Const([2.7, 3.1]))

# output

([3.1, 2.7], nothing)
```
