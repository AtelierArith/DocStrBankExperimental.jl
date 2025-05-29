```
trace!(rt)
```

Run the ray tracing simulations. This function will overwrite the `power` component of any material object that is included in the mesh. It returns the total number of rays being traced (primary and secondary) without including interactions with `Sensor` objects (first value returned) or including interactions with `Sensor` objects (second value returned). See VPL documentation for more details on the ray tracer.

## Examples

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> mat = Lambertian(τ = 0.1, ρ = 0.2);

julia> add_property!(mesh, :materials, [mat for _ in 1:ntriangles(mesh)]);

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> rt = RayTracer(mesh, source);

julia> trace!(rt);
```
