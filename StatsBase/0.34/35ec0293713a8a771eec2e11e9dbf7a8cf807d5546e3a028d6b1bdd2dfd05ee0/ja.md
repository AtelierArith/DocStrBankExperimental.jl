```
counts(x, [wv::AbstractWeights])
counts(x, levels::UnitRange{<:Integer}, [wv::AbstractWeights])
counts(x, k::Integer, [wv::AbstractWeights])
```

`x`内の各値が出現する回数をカウントします。`levels`が提供されている場合、その範囲に含まれる値のみが考慮され（他の値はエラーや警告を出さずに無視されます）、整数`k`が提供されている場合は、範囲`1:k`内の値のみが考慮されます。

重みのベクトル`wv`が提供されている場合、重みの割合が生のカウントの割合ではなく計算されます。

出力は`length(levels)`の長さのベクトルです。
