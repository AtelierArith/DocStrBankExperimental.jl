```
AxisymmetricOpticalSystem{T,C<:CSGOpticalSystem{T}} <: AbstractOpticalSystem{T}
```

Optical system which has lens elements and an image detector, created from a `DataFrame` containing prescription data.

These tags are supported for columns: `:Radius`, `:SemiDiameter`, `:SurfaceType`, `:Thickness`, `:Conic`, `:Parameters`, `:Reflectance`, `:Material`.

These tags are supported for entries in a `SurfaceType` column: `Object`, `Image`, `Stop`. Assumes the `Image` row will be the last row in the `DataFrame`.

In practice a [`CSGOpticalSystem`](@ref) is generated automatically and stored within this system.

```julia
AxisymmetricOpticalSystem{T}(
    prescription::DataFrame,
    detectorpixelsx = 1000,
    detectorpixelsy:: = 1000,
    ::Type{D} = Float32;
    temperature = AGFFileReader.TEMP_REF,
    pressure = AGFFileReader.PRESSURE_REF
)
```
