```
gradient!(::ReverseMode, dx, f, x)
```

Compute the gradient of an array-input function `f` using reverse mode, storing the derivative result in an existing array `dx`. Both `x` and `dx` must be `Array`s of the same type.

Example:

```jldoctest gradip
f(x) = x[1]*x[2]

dx = [0.0, 0.0]
gradient!(Reverse, dx, f, [2.0, 3.0])

# output
([3.0, 2.0],)
```

```jldoctest gradip
dx = [0.0, 0.0]
gradient!(ReverseWithPrimal, dx, f, [2.0, 3.0])

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```
