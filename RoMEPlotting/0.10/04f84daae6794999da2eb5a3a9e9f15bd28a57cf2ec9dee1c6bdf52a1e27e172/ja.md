```julia
plotTreeProductUp(fgl, treel, cliqsym; ...)
plotTreeProductUp(fgl, treel, cliqsym, varsym; levels, dims)

```

ベイズ/ジャンクションツリーにおける変数のプロジェクト（畳み込み）と積を取ります。

ノート

  * cliqとvarのシンボルは同じであると仮定しますが、両方が指定されている場合を除きます。
  * `cliqsym`はクリクの前面変数を定義します。
