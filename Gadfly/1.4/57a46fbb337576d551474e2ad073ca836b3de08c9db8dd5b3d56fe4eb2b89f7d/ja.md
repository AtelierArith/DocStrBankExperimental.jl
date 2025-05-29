```
hstack(ps::Union{Plot,Context}...)
hstack(ps::Vector)
```

プロットを横一列に配置します。空のパネルのプレースホルダーとして `context()` を使用します。異種ベクトルは型指定する必要があります。詳細は [`vstack`](@ref)、[`gridstack`](@ref)、および [`Geom.subplot_grid`](@ref) を参照してください。

# 例

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = Compose.context();
hstack(p1, p2)
hstack(Union{Plot,Compose.Context}[p1, p2])
```
