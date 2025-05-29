```
gradient(::ReverseMode, f, args...)
```

Compute the gradient of a real-valued function `f` using reverse mode. For each differentiable argument, this function will allocate and return new derivative object, returning a tuple of derivatives for each argument. If an argument is not differentiable, the element of the returned tuple with be nothing.

In reverse mode (here), the derivatives will be the same type as the original argument.

This is a structure gradient. For a struct `x` it returns another instance of the same type, whose fields contain the components of the gradient. In the result, `grad.a` contains `∂f/∂x.a` for any differential `x.a`, while `grad.c == x.c` for other types.

Examples:

```jldoctest gradient
f(x) = x[1]*x[2]

grad = gradient(Reverse, f, [2.0, 3.0])

# output
([3.0, 2.0],)
```

```jldoctest gradient
grad = gradient(Reverse, only ∘ f, (a = 2.0, b = [3.0], c = "str"))

# output

((a = 3.0, b = [2.0], c = "str"),)
```

```jldoctest gradient
mul(x, y) = x[1]*y[1]

grad = gradient(Reverse, mul, [2.0], [3.0])

# output
([3.0], [2.0])
```

```jldoctest gradient

grad = gradient(Reverse, mul, [2.0], Const([3.0]))

# output
([3.0], nothing)
```

If passing a mode that returns the primal (e.g. ReverseWithPrimal), the return type will instead be a tuple where the first element contains the derivatives, and the second element contains the result of the original computation.

```jldoctest gradient

grad = gradient(ReverseWithPrimal, f, [2.0, 3.0])

# output
(derivs = ([3.0, 2.0],), val = 6.0)
```

```jldoctest gradient

grad = gradient(ReverseWithPrimal, mul, [2.0], [3.0])

# output
(derivs = ([3.0], [2.0]), val = 6.0)
```

```jldoctest gradient
grad = gradient(ReverseWithPrimal, mul, [2.0], Const([3.0]))

# output
(derivs = ([3.0], nothing), val = 6.0)
```
