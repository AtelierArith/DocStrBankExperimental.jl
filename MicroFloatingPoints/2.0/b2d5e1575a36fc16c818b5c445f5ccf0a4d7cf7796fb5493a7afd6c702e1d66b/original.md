```
Floatmu{szE,szf} <: AbstractFloat
```

IEEE 754-compliant floating-point number with `szE` bits for the exponent  and `szf` bits for the fractional part.

A `Floatmu` object must always have a precision smaller or equal to that of a single precision float. As a consequence, the following constraints hold:

$$
\left\{\begin{array}{l}
\text{szE}\in[2,8]\\
\text{szf}\in[2,23]
\end{array}\right.
$$

# Examples

Creating a `Floatmu` type equivalent to `Float32`:

```jldoctest
julia> MyFloat32 = Floatmu{8,23}
Floatmu{8, 23}

julia> a=MyFloat32(0.1)
0.1

julia> a == 0.1f0
true
```
