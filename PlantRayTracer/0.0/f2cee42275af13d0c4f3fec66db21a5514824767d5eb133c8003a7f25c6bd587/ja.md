```
get_nw(s::Source)
```

ソースからの光線が含む波長の数を取得します。

## 例

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> get_nw(source);
```
