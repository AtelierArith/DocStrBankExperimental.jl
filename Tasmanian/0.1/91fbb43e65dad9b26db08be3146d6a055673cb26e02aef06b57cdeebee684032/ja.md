```
updateSequenceGrid!(tsg::TasmanianSG, depth, type; anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

は、深さ、タイプ、および異方性によって定義されたポイントを既存のグリッドに追加します。

基本的には、ルールを持つmakeSequenceGrid()を呼び出し、このグリッドの新しい深さ、タイプ、および異方性の重みを指定し、結果として得られたポイントを現在のグリッドに追加するのと同じです。

入力: help(makeSequenceGrid)を参照してください。
