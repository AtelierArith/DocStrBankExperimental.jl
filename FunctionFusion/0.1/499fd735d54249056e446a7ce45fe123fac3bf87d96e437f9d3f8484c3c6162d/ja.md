```
visualize(what, [format]; parameters...)
```

`what`のためにMIME `format`で視覚化を提供します。`what`はプロバイダーまたはプロバイダーのベクターのいずれかです。`format`が指定されていない場合は、自動的に選択されます：

  * `GraphViz`パッケージがロードされていない場合、`MIME"text/vnd.graphviz"`が選択され、これはgraphvizドキュメントです。
  * `GraphViz`パッケージがロードされている場合、`MIME"image/svg+xml"`が選択され、これは.svg画像です。

REPLでGraphVizをロードして、画像として視覚化を表示します（VScodeで自動的に表示されます）。

`parameters`：

  * `mod=Main` モジュールに対して相対的な名前を表示
  * `depth=Inf` グラフの`depth`ネストのみを表示
  * `hide_types=False` アーティファクトのタイプを隠す
