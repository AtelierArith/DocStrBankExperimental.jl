```
get_nw(rt::RayTracer)
```

レイトレーサーによってシミュレーションされている波長の数を取得します。レイトレーサーに関する詳細はVPLのドキュメントを参照してください。

## 例

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
