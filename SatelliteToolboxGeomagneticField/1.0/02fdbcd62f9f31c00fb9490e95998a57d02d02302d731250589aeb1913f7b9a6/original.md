```
igrfd(date::Number, <r, h>::T1, λ::T2, Ω::T3[, R]; kwargs...) where {T1<:Number, T2<:Number, T3<:Number} -> SVector{3, T}
```

**IGRF Model**

*Current version: v13*

Compute the geomagnetic field vector [nT] at the date `date` [Year A.D.] and position (`r` or `h`, `λ`, `Ω`).

The position representation is defined by `R`. If `R` is `Val(:geocentric)`, the input must be **geocentric** coordinates:

1. Distance from the Earth center `r` [m];
2. Geocentric latitude `λ` ∈ (-90°, +90°); and
3. Geocentric longitude `Ω` ∈ (-180°, +180°).

If `R` is `Val(:geodetic)`, the input must be **geodetic** coordinates:

1 Altitude above the reference ellipsoid `h` (WGS-84) [m];

2. Geodetic latitude `λ` ∈ (-90°, +90°); and
3. Geodetic longitude `Ω` ∈ (-180°, +180°).

If `R` is omitted, it defaults to `Val(:geocentric)`.

!!! warning
    We must have `1900 <= date <= 2030`. A warning message is printed for dates greater than 2025 since the output is not reliable anymore. This message can be suppressed by setting the keyword `show_warnings` to `false`.


!!! info
    The output vector will be represented in the same reference system selected by the parameter `R` (geocentric or geodetic). The Y-axis of the output reference system always points East. In case of **geocentric coordinates**, the Z-axis points toward the center of Earth and the X-axis completes a right-handed coordinate system. In case of **geodetic coordinates**, the X-axis is tangent to the ellipsoid at the selected location and points toward North, whereas the Z-axis completes a right-hand coordinate system.


# Keywords

  * `max_degree::Int`: Maximum degree used in the spherical harmonics when computing the   geomagnetic field. If it is higher than the available number of coefficients in the IGRF   matrices, it will be clamped. If it is equal of lower than 0, it will be set to 1.   (**Default** = 13)
  * `show_warnings::Bool`: Show warnings about the data.   (**Default** = `true`)
  * `P::Union{Nothing, AbstractMatrix}`: An optional matrix that must contain at least   `max_degree + 1 × max_degree + 1` real numbers that will be used to store the Legendre   coefficients, reducing the allocations. If it is `nothing`, the matrix will be created   when calling the function.   (**Default** = `nothing`)
  * `dP::Union{Nothing, AbstractMatrix}`: An optional matrix that must contain at least   `max_degree + 1 × max_degree + 1` real numbers that will be used to store the Legendre   derivative coefficients, reducing the allocations. If it is `nothing`, the matrix will   be created when calling the function.   (**Default** = `nothing`)

# Returns

  * `SVector{3, T}`: Geomagnetic field vector [nT] at the desired location represented in the   same input reference (geocentric or geodetic).

!!! info
    The output type `T` is obtained by promoting `T1`, `T2`, and `T3` to a float.

