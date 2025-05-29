`updateGlobalGrid!(tsg::TasmanianSG, depth, type; anisotropic*weights=Vector{Int32}(undef, 0), level*limits=Vector{Int32}(undef, 0))` は、深さ、タイプ、および異方性によって定義されたポイントを既存のグリッドに追加します。

基本的には、ルール、アルファ、ベータを持つこのグリッドの `makeGlobalGrid` を呼び出し、新しい深さ、タイプ、および異方性_weights を指定し、その後、結果として得られたポイントを現在のグリッドに追加するのと同じです。

入力: `makeGlobalGrid` のヘルプを参照してください。
