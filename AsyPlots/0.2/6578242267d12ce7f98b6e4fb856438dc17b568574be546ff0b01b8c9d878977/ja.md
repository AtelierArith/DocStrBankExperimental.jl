```
PixelMap(pixels, lowerleft, upperright; kwargs...)
```

与えられた左下隅と右上隅を持つボックス内に位置するピクセルの二次元配列を表すグラフィックスプリミティブです。

`pixels` は `NamedColor` の配列であり、`lowerleft` と `upperright` はタプルです。

# 例

```julia-repl
julia> pixels = [x*NamedColor("blue") + 
                    (1-x)*NamedColor("red") 
                        for x in 0:0.1:1, y in 0:0.1:1]
julia> PixelMap(pixels, (0,0), (1,1))
PixelMap(<11×11>,[0,1]×[0,1])
```
