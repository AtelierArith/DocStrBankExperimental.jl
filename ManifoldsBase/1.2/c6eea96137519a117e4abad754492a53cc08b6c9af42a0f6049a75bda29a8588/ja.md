```
embed(M::AbstractManifold, p)
```

点 `p` を [`AbstractManifold`](@ref) `M` から周囲空間に埋め込みます。このメソッドは、暗黙的に埋め込みまたは周囲空間が与えられている多様体に対してのみ利用可能です。さらに、`embed` はデータ表現の変更を含みます。つまり、`M` 上の点が埋め込み上の点と同じ方法で表現されていない場合、表現がそれに応じて変更されます。

デフォルトは、メモリが割り当てられ、`embed!(M, q, p)` が呼び出されるように設定されています。

関連情報: [`EmbeddedManifold`](@ref), [`project`](@ref project(M::AbstractManifold,p))
