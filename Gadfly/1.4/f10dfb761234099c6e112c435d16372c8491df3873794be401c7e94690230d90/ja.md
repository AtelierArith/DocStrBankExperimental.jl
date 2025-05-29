```
gridstack(ps::Matrix{Union{Plot,Context}})
```

プロットを長方形の配列に配置します。空のパネルのプレースホルダーとして `context()` を使用します。異種の行列は型指定する必要があります。 [`hstack`](@ref) および [`vstack`](@ref) も参照してください。

# 例

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = Compose.context();
gridstack([p1 p1; p1 p1])
gridstack(Union{Plot,Compose.Context}[p1 p2; p2 p1])
```
