```
set_xy!(h::HasseDiagram, xy::Dict{Int,Vector{T}}) where {T}
```

ハッセ図に辞書からの埋め込みを与えます。もし頂点が `xy` に現れない場合、その位置は変更されません。
