```
dX_dxdydz(composition::Union{Silicic,Mafic}, s::String, x::T, y::T, z::T)::NamedTuple{(:X, :dXdx, :dXdy, :dXdz),NTuple{4,T}} where {T<:Float64}
```

  * This function is used within the `parameters_melting_curve` function.
  * Calculate value from different parameter sets (# of parameter sets: Silicic: 3, Mafic: 2)

## Arguments

  * `composition`: `Silicic()` or `Mafic()`
  * `s`: String that represents the parameter set to use. For `Silicic`, `s` can be `"a"`, `"b"`, or `"c"`. For `Mafic`, `s` can be `"a"` or `"b"`.
  * `x`: Water (H2O)
  * `y`: Gas (CO2)
  * `z`: Pressure (P)

## Returns

A NamedTuple with the following fields:

  * `X`: the calculated value for the given parameter set
  * `dXdx`: the derivative of `X` with respect to `x`
  * `dXdy`: the derivative of `X` with respect to `y`
  * `dXdz`: the derivative of `X` with respect to `z`
