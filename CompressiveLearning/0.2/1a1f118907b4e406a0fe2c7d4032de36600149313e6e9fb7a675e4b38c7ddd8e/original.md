```julia
drawfrequencies(f, d; ...)
drawfrequencies(
    f,
    d,
    σ;
    radial_correction,
    linop_type,
    radialdist
)

```

Draws a `d`-by-`f` matrix (or equivalent fast transform) of frequencies.

  * `linop_type` can take values `:dense`, `HDHDHD`, `HGHDHD` or `fastfood`.
  * `radialdist` will be passed to `drawradiuses`.

See also: [`drawradiuses`](@ref).
