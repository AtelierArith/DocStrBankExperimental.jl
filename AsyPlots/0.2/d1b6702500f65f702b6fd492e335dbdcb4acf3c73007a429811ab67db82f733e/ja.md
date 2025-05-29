```
Plot3D(elements::Array{<:GraphicElement2D,1},
       options::Array{Any,1})
```

描画オプションと共に描画するためのグラフィックプリミティブのリストのコンテナ

# 例

```julia-repl
julia> Plot(Path([0 0 0; 1 1 1]),Path([0 0 0; 0 0 1]))
```
