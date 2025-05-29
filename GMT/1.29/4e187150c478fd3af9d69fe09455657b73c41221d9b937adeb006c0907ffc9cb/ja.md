```
setcoords!(GI::GItype; x::Vector{<:Real}=Float64[], y::Vector{<:Real}=Float64[], registration::Int=0)
```

GMTgridまたはGMTimageにx,y座標を割り当てます。`x,y`引数は必須で、[xmin, xmax]および[ymin, ymax]の2要素ベクトルであるか、`registration=0`の場合はncolumnsおよびnrowsのベクトル、または`registration=1`の場合はncolumns+1およびnrows+1のベクトルである必要があります。

### 戻り値

この関数は何も返しません。実行するのはオブジェクトの座標情報を変更することです。`setsrs!`関数も参照してください。
