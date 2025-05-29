```
Plot2D(elements::Array{<:GraphicElement,1},
       options::Array{Any,1})
```

描画オプションと共に描画するためのグラフィックプリミティブのリストのコンテナ

# 例

```julia-repl
julia> Plot([Path([0 0; 1 1]),Polygon([exp(2*pi*im*k/5) for k=1:5])])
```
