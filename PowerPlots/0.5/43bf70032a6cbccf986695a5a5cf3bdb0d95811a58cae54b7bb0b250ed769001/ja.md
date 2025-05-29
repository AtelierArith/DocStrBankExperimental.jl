```
`powerplot!(
    plt_layer::VegaLite.VLSpec, case::Dict{String,<:Any};
    layout_algorithm=kamada_kawai,
    edge_components=[:branch],
    node_components=[:bus],
    connected_components=[:gen,:load],
    fixed=false,
    kwargs...)`

地図プロットを作成し、プロットの下層に異なるVegaLiteプロットを配置します。主に、電力網の下に地理的な地図データをプロットするために使用されます。
```
