```
PlotData2D(u, semi [or mesh, equations, solver, cache];
           solution_variables=nothing,
           grid_lines=true, max_supported_level=11, nvisnodes=nothing,
           slice=:xy, point=(0.0, 0.0, 0.0))
```

`Plots.jl`を使用して2D/3D DGSEMソリューションデータ配列`u`を視覚化するために使用できる新しい`PlotData2D`オブジェクトを作成します。関連するすべての幾何学的情報は、半離散化`semi`から抽出されます。デフォルトでは、原始変数（存在する場合）または保守変数（そうでない場合）がプロットに使用されます。これは、適切な変換関数を`solution_variables`に渡すことで変更できます。

`grid_lines`が`true`の場合、メッシュを視覚化するためにグリッド頂点も抽出されます。出力解像度は`max_supported_level`を介して間接的に設定されます：すべてのデータは、各空間方向に均等に分布した`2^max_supported_level`のポイントに補間され、ソリューションの最大許可される細分化レベルも設定されます。`nvisnodes`は、使用される視覚化ノードの数を指定します。`nothing`の場合、視覚化にはソリューションDGノードの2倍の数が使用され、`0`に設定された場合は、DG要素内のノードの正確な数が使用されます。

三次元シミュレーションからデータを視覚化する際には、プロット用に2Dスライスが抽出されます。`slice`はスライスされる平面を指定し、`:xy`、`:xz`、または`:yz`のいずれかになります。スライス位置は、デフォルトで`(0.0, 0.0, 0.0)`となる`point`によって指定されます。これらの値は、2Dデータを視覚化する際には無視されます。

!!! warning "実験的な実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


# 例

```julia
julia> using Trixi, Plots

julia> trixi_include(default_example())
[...]

julia> pd = PlotData2D(sol)
PlotData2D(...)

julia> plot(pd) # 利用可能なすべての変数をプロットするために

julia> plot(pd["scalar"]) # 単一の変数のみをプロットするために

julia> plot!(getmesh(pd)) # プロットにグリッド線を追加するために
```
