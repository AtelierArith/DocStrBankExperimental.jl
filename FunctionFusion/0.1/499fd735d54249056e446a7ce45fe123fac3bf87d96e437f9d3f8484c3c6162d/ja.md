```
visualize(what, [format]; parameters...)
```

`what`のMIME `format`での視覚化を提供します。`what`はプロバイダーまたはプロバイダーのベクターのいずれかです。`format`が指定されていない場合は、自動的に選択されます：

  * `GraphViz`パッケージがロードされていない場合、これは`MIME"text/vnd.graphviz"`であり、グラフvizドキュメントです。
  * `GraphViz`パッケージがロードされている場合、これは`MIME"image/svg+xml"`であり、.svg画像です。

REPLでGraphVizをロードして、画像として視覚化を表示します（VScodeで自動的に表示されます）。

`parameters`：

  * `mod=Main` そのモジュールに対して相対的な表示名
  * `depth=Inf` グラフの`depth`ネストのみを表示
  * `hide_types=False` アーティファクトのタイプを非表示にする

```
