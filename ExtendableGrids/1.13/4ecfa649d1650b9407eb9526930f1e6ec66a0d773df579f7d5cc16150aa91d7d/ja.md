```
grid_triangle(coords::AbstractArray{T,2}) where {T}
```

与えられた座標を使用して単一の三角形を生成します。これは、3つの頂点の座標を持つ2 x 3の配列である必要があります。例えば、coords = [0.0 0.0; 1.0 0.0; 0.0 1.0]'。
