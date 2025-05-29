```
project(M::AbstractManifold, p)
```

点 `p` を、[`AbstractManifold`](@ref) `M` の周囲空間から `M` に射影します。このメソッドは、暗黙的に埋め込みまたは周囲空間が与えられているマニホールドに対してのみ利用可能です。さらに、射影にはデータ表現の変更が含まれます。つまり、`M` 上の点が同じ配列データで表現されていない場合、データはそれに応じて変更されます。

関連情報: [`EmbeddedManifold`](@ref), [`embed`](@ref embed(M::AbstractManifold, p))
