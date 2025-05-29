```
function randomTTN(sites::Vector{Index{T}}, graph::Graph{Int2},
                   sitenodes::Dict{Int, Int2}, chi::Int, qn::QN = QN()) where T
```

サイト `Index`s `sites`、基盤となる `graph`、各サイトを対応するノードにマッピングする `sitenodes::Dict{Int, Int2}`、初期ボンド次元 `chi`、および（オプションの）グローバル QN セクター `qn` から、ランダムな要素を持つ TTN オブジェクトを返します。構造は入力された `graph` オブジェクトによって決定されます。

**注意**: この関数は、ループのないテンソルネットワークを生成するために使用できます。

**注意**: QN 保存 TTN の場合、ボンド次元は `chi` から1または2オフになる可能性があります。
