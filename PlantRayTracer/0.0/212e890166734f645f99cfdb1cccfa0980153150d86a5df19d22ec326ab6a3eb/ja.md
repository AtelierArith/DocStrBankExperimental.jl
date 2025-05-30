```
trace!(rt)
```

レイトレーシングシミュレーションを実行します。この関数は、メッシュに含まれる任意の材料オブジェクトの `power` コンポーネントを上書きします。これは、センサーオブジェクトとの相互作用を含まない（最初に返される値）またはセンサーオブジェクトとの相互作用を含む（2番目に返される値）トレースされる光線の総数を返します。レイトレーサーに関する詳細はVPLドキュメントを参照してください。

## 例

```jldoctest
julia> using PlantGeomPrimitives;

julia> mesh = Ellipse();

julia> mat = Lambertian(τ = 0.1, ρ = 0.2);

julia> add_property!(mesh, :materials, [mat for _ in 1:ntriangles(mesh)]);

julia> source = DirectionalSource(mesh, θ = 0.0, Φ = 0.0, radiosity = 1.0, nrays = 1_000);

julia> rt = RayTracer(mesh, source);

julia> trace!(rt);
```
