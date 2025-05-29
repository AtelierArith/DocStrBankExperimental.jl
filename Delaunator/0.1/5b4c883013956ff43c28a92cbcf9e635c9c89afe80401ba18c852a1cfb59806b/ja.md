```
bt, cdata = basictriangulation(IntType=Int32,] [FloatType=Float64,] [points];[sizehint=length(points),] [tol])
```

基本的な三角形分割構造体と関連する計算データを割り当てて、デローニ法を実装します。

**この方法は実際には三角形分割を計算するのではなく、データを割り当てるだけです。計算メソッドについては `triangulate` または `update!` を参照してください。**

## 三角形分割データ構造

これらのデータ構造は https://mapbox.github.io/delaunator/ で説明されています（ただし、ここではすべてのインデックスが少し変更されています）。

  * `triangles`: 各タプルが三角形である長さ T の配列
  * `halfedges`: 三角形配列内の辺のためのハーフエッジインデックス。三角形 t のハーフエッジは 3(t-1)+1, 3(t-1)+2, 3(t-2)+3 です。各ハーフエッジインデックスは他のハーフエッジのエントリを示します。
  * `points`: 入力された点のセットのコピー
