```
changeMapping(pb::ParamBox{T, V}, mapFunction::Function=itself, outSym::Symbol=V; 
              canDiff::Union{Bool, Array{Bool, 0}}=isDiffParam(pb)) where {T, V} -> 
ParamBox{T, outSym}
```

`pb`のマッピング関数を変更します。返される`ParamBox`の出力変数のシンボルは`outSym`で指定でき、その微分可能性は`canDiff`によって決まります。
