`setprop!`のバリエーションで、基盤となるJSプロパティの明示的な型を受け入れます。このプロパティ型はアニメーションコンテキスト内でのみ使用されます。

```julia
setprop!(
    vis::MeshCat.Visualizer,
    property::AbstractString,
    jstype::AbstractString,
    value
) -> MeshCat.Visualizer

```
