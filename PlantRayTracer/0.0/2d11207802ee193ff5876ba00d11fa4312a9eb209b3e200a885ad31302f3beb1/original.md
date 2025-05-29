```
get_nw(rt::RayTracer)
```

Retrieve the number of wavelengths being simulated by the ray tracer. See VPL documentation for more details on the ray tracer.

## Examples

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> mat = Lambertian(τ = 0.1, ρ = 0.2);

julia> add_property!(mesh, :materials, [mat for _ in 1:ntriangles(mesh)]);

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> rt = RayTracer(mesh, source);

julia> get_nw(rt)
1
```
