```
updateFourierGrid!(tsg::TasmanianSG, depth, type; anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

は、深さ、タイプ、および異方性によって定義されたポイントを既存のグリッドに追加します。

基本的には、ルールを持つ `makeFourierGrid()` を呼び出し、このグリッドの新しい深さ、タイプ、および異方性重みを使用して、結果として得られたポイントを現在のグリッドに追加するのと同じです。

入力: `makeGlobalGrid` のヘルプを参照してください。
