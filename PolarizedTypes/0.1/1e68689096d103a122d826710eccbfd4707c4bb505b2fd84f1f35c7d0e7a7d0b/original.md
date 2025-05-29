```julia
polellipse(s)

```

Returns the polarization ellipse of the Stokes parameters `s`. The results is a named tuple with elements

  * `a`   : The semi-major axis of the polarization ellipse
  * `b`   : The semi-minor axis of the polarization ellipse
  * `evpa`: The electric vector position angle of `s` or the PA of the ellipse.
  * `sn`  : The sign of the Stokes `V`.

## Notes

The semi-major and semi-minor axes are defined as

```
    a = 1/2(Iₚ + |L|)
    b = 1/2(Iₚ - |L|)
```

where `Iₚ = √(Q² + U² + V²)` and `|L| = √(Q² + U²)`.

In general the area of the ellipse is given by

```
    πab = π/4|V|²
```

For sources with zero linear polarization `a = b` so we have a circle with radius `|V|`. For purely linear polarization `b = 0` giving a line with length `|L|`.
