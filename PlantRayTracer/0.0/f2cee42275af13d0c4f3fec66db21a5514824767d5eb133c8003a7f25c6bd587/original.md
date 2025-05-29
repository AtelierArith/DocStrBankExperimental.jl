```
get_nw(s::Source)
```

Retrieve the number of wavelengths that rays from a source will contain.

## Examples

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> get_nw(source);
```
