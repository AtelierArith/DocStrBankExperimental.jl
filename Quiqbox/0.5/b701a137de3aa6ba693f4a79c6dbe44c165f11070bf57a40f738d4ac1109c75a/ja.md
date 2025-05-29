```
outValCopy(pb::ParamBox{T, V}) where {T} -> ParamBox{T, V, typeof(Quiqbox.itself)}
```

入力変数の値が `pb` の出力変数の値と等しい新しい `ParamBox` を返します。
