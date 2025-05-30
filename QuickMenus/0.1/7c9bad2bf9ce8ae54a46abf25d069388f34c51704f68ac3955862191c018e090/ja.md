```
quickmenu([indexer, ℳ,] itr;
          message="", cursor=1, charset=:unicode, kw...)
```

ユーザーに反復可能な `itr` から要素を選択するためのターミナルメニューを表示します。

`QuickMenus` によって提供されるエイリアス `qm`（単一選択用）または `qmm`（複数選択用）があります。

## 引数

  * `itr`: 要素を選択するための反復可能なオブジェクト。
  * `indexer`: 反復可能な `itr` のインデックス付けに使用される関数。デフォルトは `getindex`。
  * `ℳ`: ターミナルメニューのタイプ、`RadioMenu` または `MultiSelectMenu`。
  * `message`: 選択メニューの前に表示するメッセージ。
  * `cursor`: 初期カーソル位置。
  * `charset`: ターミナルメニューに使用する文字セット。
  * `kw`: ターミナルメニューコンストラクタ `ℳ` に提供される追加のキーワード引数。
