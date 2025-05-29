```
triangulate(X::LazySet; [algorithm]::String="delaunay", [kwargs]...)
```

与えられた多面体集合の三角形分割を計算します。

### 入力

  * `X`         – 多面体集合
  * `algorithm` – （オプション; デフォルト: `delaunay`）三角形分割の種類を選択するための文字列
  * `kwargs`    – アルゴリズムに渡されるさらなるキーワード引数

### 出力

頂点表現の多面体の和。

### アルゴリズム

アルゴリズムは引数 `algorithm` で選択されます。

  * `"delaunay"`: このアルゴリズムはデローニ三角形分割を計算します。

このアルゴリズムは、`compute_triangles_3d` という別のオプション引数を受け取ることができ、デフォルトは `false` です。これは、`true` の場合に3D集合の2D三角形分割を計算するために使用されます。

実装には、ライブラリ [Qhull](http://www.qhull.org/) を使用するパッケージ [MiniQhull.jl](https://github.com/gridap/MiniQhull.jl) が必要です。

このアルゴリズムは任意の次元で動作し、`X` の頂点のリストを取得できる必要があります。
