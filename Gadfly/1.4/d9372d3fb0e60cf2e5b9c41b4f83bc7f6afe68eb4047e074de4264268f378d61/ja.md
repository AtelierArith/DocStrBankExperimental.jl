```
vstack(ps::Union{Plot,Context}...)
vstack(ps::Vector)
```

プロットを垂直列に配置します。空のパネルのプレースホルダーとして `context()` を使用します。異種ベクトルは型指定する必要があります。 [`hstack`](@ref)、[`gridstack`](@ref)、および [`Geom.subplot_grid`](@ref) も参照してください。

# 例

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = Compose.context();
vstack(p1, p2)
vstack(Union{Plot,Compose.Context}[p1, p2])
```
