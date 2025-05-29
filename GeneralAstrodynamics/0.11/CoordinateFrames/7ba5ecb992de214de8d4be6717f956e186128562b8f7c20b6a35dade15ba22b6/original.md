```julia
struct Transform{F1<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, F2<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, T1<:CoordinateTransformations.Transformation, T2<:CoordinateTransformations.Transformation} <: GeneralAstrodynamics.CoordinateFrames.OrbitalFrameTransform
```

```julia
struct Transform{F1<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, F2<:GeneralAstrodynamics.CoordinateFrames.OrbitalFrame, T1<:CoordinateTransformations.Transformation, T2<:CoordinateTransformations.Transformation} <: GeneralAstrodynamics.CoordinateFrames.OrbitalFrameTransform
```

A generic frame transformation between two `OrbitalFrame` types. Converts `F1` to`F2`.

  * `transform_position::CoordinateTransformations.Transformation`
  * `transform_velocity::CoordinateTransformations.Transformation`
