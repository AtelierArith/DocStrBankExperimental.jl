```
メッシュ、ソースのタプル（`Source`から継承したオブジェクト）または単一のソース、設定、および加速関数（`Naive`または`BVH`から選択）を使用して`RayTracer`オブジェクトを作成します。引数`rule`は加速器`BVH`にのみ必要であり、`SAH`または`AvgSplit`型のオブジェクトでなければなりません（`Naive`加速器の場合は無視されます）。

## 例

```

jldoctest julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> mat = Lambertian(τ = 0.1, ρ = 0.2);

julia> add_property!(mesh, :materials, [mat for _ in 1:ntriangles(mesh)]);

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> rt = RayTracer(mesh, source);

julia> sources = (DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1*000),                   DirectionalSource(mesh, θ = 45.0, Φ = 0.0, radiosity = 1.0, nrays = 1*000));

julia> rt = RayTracer(mesh, sources); ```
