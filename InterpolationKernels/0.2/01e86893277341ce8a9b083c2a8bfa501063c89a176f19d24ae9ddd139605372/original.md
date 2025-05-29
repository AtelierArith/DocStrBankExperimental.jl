# Interpolation Kernels

An interpolation kernel `Kernel{T,S}` is parameterized by the floating-point type `T` of its coefficients and by the integer size `S` of its support.  For efficiency reasons, only kernels with (small) finite size supports are implemented in `InterpolationKernels`.

A kernel `ker` is a callable object which may be used as a function with a real argument:

```
ker(x::Real)
```

yields kernel value at offset `x`.  Whatever the type of `x`, `ker(x)` is always of type `T = eltype(ker)` the floating-point type associated with `ker`. All kernel supports are symmetric; that is `ker(x)` is zero if `abs(x) > S/2` with `S = length(ker)` the size of the kernel support.

## Kernel floating-point type conversion

Called as a function with a real argument, a given kernel returns a value of its associated floating-point type.  This has been chosen to have fast interpolation methods.  Converting a kernel `ker` to use floating-point type `T` is simply done by one of:

```
T(ker)
Kernel{T}(ker)
convert(Kernel{T}, ker)
```

Beware that changing the floating-point type may lead to a loss of precision if the kernel has numerical parameters.

## Common methods

A few common methods are specialized for any interpolation kernel `ker`:

```
eltype(ker) -> T
```

yields the floating-point type for calculations,

```
length(ker) -> S
```

yield the size the support of `ker` which is also the number of neighbors involved in an interpolation by this kernel,

```
values(ker)
```

yields a tuple of the parameters of `ker` such that an identical instance can be built by:

```
typeof(ker)(values(ker)...)
```

finally:

```
compute_offset_and_weights(ker, x) -> off, (w1, w2, ..., wS)
```

yields the offset `off` and an `S`-tuple of interpolation weights to interpolate an array at coordinate `x` (in fractional index units).
