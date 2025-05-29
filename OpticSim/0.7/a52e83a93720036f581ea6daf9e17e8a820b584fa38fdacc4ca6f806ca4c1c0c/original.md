```
CSGOpticalSystem{T,D<:Real,S<:Surface{T},L<:LensAssembly{T}} <: AbstractOpticalSystem{T}
```

An optical system containing a lens assembly with all optical elements and a detector surface with associated image. The system can be at a specified temperature and pressure.

There are two number types in the type signature. The `T` type parameter is the numeric type for geometry in the optical system, the `D` type parameter is the numeric type of the pixels in the detector image. This way you can have `Float64` geometry, where high precision is essential, but the pixels in the detector can be `Float32` since precision is much less critical for image data, or Complex if doing wave optic simulations.

The detector can be any [`Surface`](@ref) which implements [`uv`](@ref), [`uvtopix`](@ref) and [`onsurface`](@ref), typically this is one of [`Rectangle`](@ref), [`Ellipse`](@ref) or [`SphericalCap`](@ref).

```julia
CSGOpticalSystem(
    assembly::LensAssembly,
    detector::Surface,
    detectorpixelsx = 1000,
    detectorpixelsy = 1000, ::Type{D} = Float32;
    temperature = AGFFileReader.TEMP_REF,
    pressure = AGFFileReader.PRESSURE_REF
)
```
