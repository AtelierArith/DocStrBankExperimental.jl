```
GRPFParams
```

`RootsAndPoles`によって反復を停止したり、Delaunay三角形を分割するために使用される値を保持するための構造体です。

デフォルト値は`GRPFParams()`によって提供されます。

# フィールド

  * `maxiterations::Int = 100`: `grpf`が返る前の最大反復回数。
  * `maxnodes::Int = 500000`: `grpf`が返る前の最大Delaunayタイルノード数。
  * `skinnytriangle::Int = 3`: Delaunay三角形が`grpf`の反復中に分割される前の、最長辺と最短辺の長さの最大比。
  * `tess_sizehint::Int = 5000`: Delaunayタイルの期待されるノードの総数に対するサイズヒントを提供します。この数をおおよそ正確に設定することで、パフォーマンスが向上する可能性があります。
  * `tolerance::Float64 = 1e-9`: 戻る前に`origcoords`ドメインで定義されたタイルの最大許容辺の長さ。
  * `multithreading::Bool = false`: `Threads.@threads`を使用して、ユーザー提供の関数`fcn`を`DelaunayTriangulation`全体で実行します。
