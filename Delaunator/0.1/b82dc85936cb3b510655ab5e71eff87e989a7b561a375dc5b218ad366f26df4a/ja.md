```
triangulate([Int32,] [FloatType=Float64,] points; [tol=eps(FloatType),])
```

Delaunatorアルゴリズムを使用して、一連の点の三角形分割を計算します。これは、正確な計算幾何学よりも迅速なグラフィックスアプリケーションと速度のために設計されています。

## 入力

  * `points` は、整数インデックスと長さがサポートされている任意の型です。さらに、`p = points[i]` は、`p[1]` と `p[2]` が p の x, y 座標である型である必要があります。または、独自の型 p のために `Delaunator.getX(p), Delaunator.getY(p)` 関数を定義する必要があります。

    点情報を提供するために行列を使用したい場合は、[`PointsFromMatrix`](@ref)
  * `tol` は、点が十分に近いと見なされるかどうかを判断するために使用されます。

## 戻り値

エッジ、ハルポイント、双対セルを探索するためのメソッドを持つ三角形分割。

さらに [`basictriangulation`](@ref) を参照してください。
