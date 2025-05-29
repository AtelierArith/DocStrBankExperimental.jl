```
RayTracer(mesh, sources; settings = RTSettings(), acceleration = Naive, rule = nothing)
```

Create a `RayTracer` object from a mesh, a tuple of sources (objects that inherit from `Source`), or a single source, settings and acceleration function (choose from `Naive` or  `BVH`). The argument `rule` is only required for the accelerator `BVH` and it must be an object of type `SAH` or `AvgSplit` (it is ignored for the `Naive` accelerator).

## Examples

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> mat = Lambertian(τ = 0.1, ρ = 0.2);

julia> add_property!(mesh, :materials, [mat for _ in 1:ntriangles(mesh)]);

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> rt = RayTracer(mesh, source);

julia> sources = (DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000),
                  DirectionalSource(mesh, θ = 45.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000));

julia> rt = RayTracer(mesh, sources);
```
