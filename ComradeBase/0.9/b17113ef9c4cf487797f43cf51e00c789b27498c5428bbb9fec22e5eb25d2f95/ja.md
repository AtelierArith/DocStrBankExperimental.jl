```
UnstructuredMap(data::AbstractVector, dims::UnstructuredDomain)
```

非構造ドメイン上で定義されたマップです。これは通常、値のベクトルに過ぎません。可視性の位置のベクトルは `dims` に格納されています。それ以外は、グリッドではないことを除いて、`IntensityMap` と非常に似た動作をします。

たとえば、可視性の位置には `axisdims` を使用してアクセスでき、通常の `getproperty` および `propertynames` 関数も使用できます。`IntensityMap` と同様に、実行中は `executor` が実行コンテキストを決定するために使用されます。
