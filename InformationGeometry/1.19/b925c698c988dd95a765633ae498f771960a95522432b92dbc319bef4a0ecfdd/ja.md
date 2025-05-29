```
InterpolatedProfiles(M::AbstractVector{<:AbstractMatrix}, Interp::Type{<:AbstractInterpolation}=QuadraticInterpolation) -> Vector{Function}
```

`ParameterProfiles`の`Vector{Matrix}`出力を補間します。 !!!注意     プロファイル内の収束した点と非収束の点を区別しません。
