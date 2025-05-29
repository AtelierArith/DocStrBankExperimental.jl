```
project!(M::AbstractManifold, q, p)
```

点 `p` を周囲空間から [`AbstractManifold`](@ref) `M` に射影します。結果は `q` に格納されます。このメソッドは、暗黙的に埋め込みまたは周囲空間が与えられているマニホールドに対してのみ利用可能です。さらに、射影にはデータ表現の変更が含まれます。つまり、`M` 上の点が同じ配列データで表現されていない場合、データはそれに応じて変更されます。

関連情報: [`EmbeddedManifold`](@ref), [`embed!`](@ref embed!(M::AbstractManifold, q, p))
