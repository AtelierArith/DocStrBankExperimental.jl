```julia
struct Transform{F1<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, F2<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, T1<:CoordinateTransformations.Transformation, T2<:CoordinateTransformations.Transformation} <: GeneralAstrodynamics.CoordinateFrames.OrbitalFrameTransform
```

```julia
struct Transform{F1<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, F2<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, T1<:CoordinateTransformations.Transformation, T2<:CoordinateTransformations.Transformation} <: GeneralAstrodynamics.CoordinateFrames.OrbitalFrameTransform
```

2つの`OrbitalFrame`タイプ間の一般的なフレーム変換。`F1`を`F2`に変換します。

  * `transform_position::CoordinateTransformations.Transformation`
  * `transform_velocity::CoordinateTransformations.Transformation`
