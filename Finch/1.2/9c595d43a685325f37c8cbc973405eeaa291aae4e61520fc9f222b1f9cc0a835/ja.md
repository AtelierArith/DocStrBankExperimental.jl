```
offset(tns, delta...)
```

`OffsetArray`を作成します。ここで、`offset(tns, delta...)[i...] == tns[i .+ delta...]` です。`OffsetArray`によって宣言された次元はシフトされるため、`size(offset(tns, delta...)) == size(tns) .+ delta` となります。
