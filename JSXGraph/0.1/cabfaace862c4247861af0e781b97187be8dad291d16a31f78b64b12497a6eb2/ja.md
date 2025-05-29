```
board(name="brd"+randstring(3); opts...)
```

新しいボードを作成します。

  * `name` - ボードの名前（デフォルトで生成されます）

## キーワード

  * `xlim::Vector` - x軸の制限 デフォルト: `[-10,10]`
  * `ylim::Vector` - y軸の制限 デフォルト: `[-10,10]`
  * `axis::Bool` - 軸を表示するかどうか 例: false
  * `showcopyright::Bool` - JSXの著作権を表示するかどうか 例: true
  * `shownavigation::Bool` - ボード上にナビゲーションツールを表示するかどうか 例: true
  * `style::String` - ボードを含むdivのCSSスタイル 例: `"width:300px; height:300px;"`

https://jsxgraph.org/docs/symbols/JXG.Board.html のキーワードも使用できます。
