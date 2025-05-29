```
CF = floattype(C::Type)
```

色素タイプ `C` のストレージデータ型を `AbstractFloat` に昇格させつつ、`base_colorant_type` は同じままにします。

!!! info
    非パラメトリック色素は、対応するパラメトリック色素に昇格されます。例えば、`floattype(RGB24) == RGB{Float32}` です。

