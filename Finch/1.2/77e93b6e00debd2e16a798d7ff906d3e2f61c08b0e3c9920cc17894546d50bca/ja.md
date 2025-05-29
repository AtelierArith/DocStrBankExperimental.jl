```
scale(tns, delta...)
```

`ScaleArray`を作成して、`scale(tns, delta...)[i...] == tns[i .* delta...]`となるようにします。OffsetArrayによって宣言された次元はシフトされるため、`size(scale(tns, delta...)) == size(tns) .* delta`となります。これは実数値の次元を持つテンソルにのみサポートされています。
