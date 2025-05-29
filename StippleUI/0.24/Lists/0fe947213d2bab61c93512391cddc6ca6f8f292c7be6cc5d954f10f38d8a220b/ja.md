```
  list(args...; kwargs...)
```

`list` と `item` は、複数の行アイテムを縦に連続した単一の要素として表示するために一緒に機能するコンポーネントのグループです。これらは、連絡先リスト、プレイリスト、またはメニューなど、情報の行として表示するのに最適です。各行は Item と呼ばれます。`item` は `list` の外でも使用できます。

---

### 例

---

### 表示

```julia-repl
julia>  list(bordered=true, separator=true, [
          item(clickable=true, vripple=true, [
            itemsection("シングルラインアイテム")
          ]),

          item(clickable=true, vripple=true, [
            itemsection([
              itemlabel("キャプション付きアイテム"),
              itemlabel("キャプション", caption=true)
            ])
          ]),

          item(clickable=true, vripple=true, [
            itemsection([
              itemlabel("オーバーライン", overline=true),
              itemlabel("キャプション付きアイテム")
            ])
          ])
        ])
```

---

### 引数

---

1. コンテンツ

      * `separator::Bool` - 含まれるアイテムの間にセパレーターを適用します
      * `padding:Bool` - 上下にマテリアルデザインのようなパディングを適用します
2. スタイル

      * `bordered::Bool` - コンポーネントにデフォルトのボーダーを適用します
      * `dense::Bool` - 密なモード; より少ないスペースを占有します
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
