```
Acf <: AbstractFloat
```

Complex arbitrary precision floating point number type.

The internal representation of the real and imaginary parts are the same as for [`Arf`](@ref). It is a wrapper of the type [`acf`](https://flintlib.org/doc/acf.html) in Flint.

See also [`AcfRef`](@ref) for handling pointers to `acf` objects and [`Acb`](@ref) for a complex number type with rigorous error tracking.

!!! note "Limited capabilities"
    The `Acf` type only implements very basic functionalities. For most purposes it is better to use the [`Acb`](@ref) type, this is true even in situations where the rigorous error tracking done by `Acb` is not needed.

