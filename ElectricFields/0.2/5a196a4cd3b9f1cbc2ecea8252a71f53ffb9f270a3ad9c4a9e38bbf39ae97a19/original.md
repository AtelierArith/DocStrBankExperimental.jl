```
DispersedField(f, de, B, s)
```

Represents the field `f` dispersed through the [`DispersiveElement`](@ref) `de`. Since the dispersion is most efficiently calculated in the frequency domain, this is done via [`rfft`](@ref)/[`irfft`](@ref), and the dispersed field is interpolated as the [`BSplineField`](@ref) `B`. The temporal [`span`](@ref) of the dispersed field is given by `s`.
