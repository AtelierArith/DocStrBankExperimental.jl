```
function default_randomTTN(sites::Vector{Index{T}}, chi::Int, qn::QN = QN()) where T
```

サイト `Index`s `sites` から、初期ボンド次元 `chi` と (オプションの) グローバル QN セクター `qn` を持つランダム要素を持つ TTN オブジェクトを返します。構造はデフォルトの階層的二分木グラフです。サイトの数が 2 の累乗でない場合も自動的に処理します。

**注意**: QN 保存 TTN の場合、ボンド次元は `chi` から 1 または 2 ずれる可能性があります。
