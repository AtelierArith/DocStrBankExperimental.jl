```
flipgraph(g::TriangulatedPolygon; kwargs..)
```

`TriangulatedPolygon` `g` の **`FlipGraph`** を構築します。

# 引数

  * 'modular::Bool = false' : デフォルトでは、全体のフリップグラフが構築されます。`modular` が `true` に設定されている場合、モジュラー フリップグラフのみが構築されます。

*モジュラー フリップグラフ* では、フリップグラフの頂点は、頂点の名前変更に対して同型のクラスです。各クラスは、その要素の1つによって表されます。
