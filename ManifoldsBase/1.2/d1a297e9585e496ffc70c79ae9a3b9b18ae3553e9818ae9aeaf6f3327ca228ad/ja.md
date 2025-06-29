```
project!(M::AbstractManifold, Y, p, X)
```

ベクトル `X` の周囲空間表現を、[`AbstractManifold`](@ref) `M` の点 `p` における接ベクトルに射影します。結果はベクトル `Y` に保存されます。このメソッドは、暗黙的に埋め込みまたは周囲空間が与えられている多様体に対してのみ利用可能です。さらに、`project!` には、データ表現の変更が含まれます。つまり、`M` 上の接ベクトルが埋め込み上の点と同じ方法で表現されていない場合、表現がそれに応じて変更されます。これは、接ベクトルがリー代数で表現されるリー群のような場合に該当します。射影後、リー代数への変更も行われます。

関連情報: [`EmbeddedManifold`](@ref), [`embed!`](@ref embed!(M::AbstractManifold, Y, p, X))
