```
DirectionalSource(box::AABB; θ, Φ, radiosity, nrays)
DirectionalSource(mesh::Mesh; θ, Φ, radiosity, nrays)
```

Create a Directional source (including geometry and angle components) by providing an axis-aligned bounding box (`box`) or an `Mesh` object  as well as the zenith (`θ`) and azimuth (`Φ`) angles, the radiosity of the source projected on the horizontal plane and the number of rays to be generated. Directional sources may generate incorrect results in the absence of a grid cloner that extends the mesh. This is because the rays are generated from the upper face of the mesh's bounding box. See VPL documentation for details on light sources.

## Examples

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);
```
