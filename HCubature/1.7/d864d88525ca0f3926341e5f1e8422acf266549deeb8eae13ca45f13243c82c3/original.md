```
hcubature(f, a, b; norm=norm, rtol=sqrt(eps), atol=0, maxevals=typemax(Int),
initdiv=1, buffer=nothing)
```

Compute the n-dimensional integral of f(x), where `n == length(a) == length(b)`, over the hypercube whose corners are given by the vectors (or tuples) `a` and `b`. That is, dimension `x[i]` is integrated from `a[i]` to `b[i]`.  The return value of `hcubature` is a tuple `(I, E)` of the estimated integral `I` and an estimated error `E`.

`f` should be a function `f(x)` that takes an n-dimensional vector `x` and returns the integrand at `x`.   The integrand can be any type that supports `+`, `-`, `*` real, and `norm` functions.  For example, the integrand can be real or complex numbers, vectors, matrices, etcetera.

The integrand `f(x)` will be always be passed an `SVector{n,T}`, where `SVector` is an efficient vector type defined in the `StaticArrays` package and `T` is a floating-point type determined by promoting the endpoint `a` and `b` coordinates to a floating-point type. (Your integrand `f` should be type-stable: it should always return a value of the same type, given this type of `x`.)

The integrand will never be evaluated exactly at the boundaries of the integration volume.  (So, for example, it is possible to have an integrand that blows up at the boundaries, as long as the integral is finite, though such singularities will slow convergence.)

The integration volume is adaptively subdivided, using a cubature rule due to Genz and Malik (1980), until the estimated error `E` satisfies `E ≤ max(rtol*norm(I), atol)`, i.e. `rtol` and `atol` are the relative and absolute tolerances requested, respectively. It also stops if the number of `f` evaluations exceeds `maxevals`. If neither `atol` nor `rtol` are specified, the default `rtol` is the square root of the precision `eps(T)` of the coordinate type `T` described above. Initially, the volume is divided into `initdiv` segments along each dimension.

The error is estimated by `norm(I - I′)`, where `I′` is an alternative estimated integral (via an "embedded" lower-order cubature rule.) By default, the norm function used (for both this and the convergence test above) is `norm`, but you can pass an alternative norm by the `norm` keyword argument.  (This is especially useful when `f` returns a vector of integrands with different scalings.)

In normal usage, `hcubature(...)` will allocate a buffer for internal computations. You can instead pass a preallocated buffer allocated using [`hcubature_buffer'](@ref) as the `buffer` argument. This buffer can be used across multiple calls to avoid repeated allocation.
