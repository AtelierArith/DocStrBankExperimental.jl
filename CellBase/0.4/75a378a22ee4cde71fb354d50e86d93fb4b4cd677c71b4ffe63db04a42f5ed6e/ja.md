構成を表す型

Composition型はインデックスアクセスをサポートしています：

```julia-repl
julia> comp = Composition(:CO2)
Composition(:CO2)
julia> comp[:C] 
1
```

内部的には、種と量は2つのベクターとして保存されていますが、インターフェースは`Dict{Sybmol,Float64}`のものを模倣しています。
