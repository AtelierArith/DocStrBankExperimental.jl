# Interpolation Kernels

An interpolation kernel `Kernel{T,S,B}` is parametrized by the floating-point type `T` of its coefficients, by the size `S` of its support and by the boundary conditions `B` to apply for extrapolation.  For efficiency reasons, only kernels with (small) finite size supports are implemented.

A kernel `ker` is a callable object which may be used as a function with a real argument:

```
ker(x::Real)
```

yields kernel value at offset `x`.  All kernel supports are symmetric; that is `ker(x)` is zero if `abs(x) > S/2` with `S` the size of the kernel support.

## Kernel conversion

The argument of a kernel be a floating-point type and/or a boundary conditions type:

```
ker(::Type{T}, ::Type{B}) where {T<:AbstractFloat, B<:Boundaries}
```

to convert the kernel to operate with given floating-point type `T` and use boundary conditions `B` (any of which can be omitted and their order is irrelevant).  Beware that changing the floating-point type may lead to a loss of precision if the new floating-point type has more digits).

It is possible to change the floating-point type of a kernel or its boundary conditions by something like:

```julia
Float32(ker)    # change floating-point type of kernel `ker`
SafeFlat(ker)   # change boundary conditions of kernel `ker`
```

The above calls do not follow the usuall conventions that a constructor may be called to convert its argument(s) to an instance of its type, this is however practical considering the following more rigorous calls to repectively change the the floating-point type and boundary conditions of kernel `ker`:

```julia
convert(Kernel{Float32}, ker)
convert(Kernel{eltype(ker),length(ker),SafeFlat}, ker)
```

## Available methods

The following methods are available for any interpolation kernel `ker`:

```julia
eltype(ker) -> T
```

yields the floating-point type for calculations,

```julia
length(ker) -> S
size(ker)   -> (S,)
```

yield the size the support of `ker` which is also the number of neighbors involved in an interpolation by this kernel,

```julia
boundaries(ker) -> B
```

yields the type of the boundary conditions applied for extrapolation; finally:

```julia
getweights(ker, t) -> w1, w2, ..., wS
```

yields the `S` interpolation weights for offset `t`

```
t = x - floor(x)        if s is even
    x - round(x)        if s is odd
```

`t ∈ [0,1]` if `S` is even or for offset `t ∈ [-1/2,+1/2]` if `S` is odd.
