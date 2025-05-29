```
badge()
```

`badge` コンポーネントは、目立たせて注目を集める必要があるコンテキストデータのような情報を追加するための小さなバッジを作成することを可能にします。また、ユーザーアバターなどの他の要素と組み合わせて、新しいメッセージの数を表示するのにもよく役立ちます。

---

### 例

---

### モデル

```julia-repl
julia> @vars BadgeModel begin
          myicon = "bluetooth"
       end
```

### ビュー

```julia-repl
julia> Html.div("Badge", class="text-h6", [
          badge("1.0.0+", color="primary")
       ])
```

---

### 引数

---

1. コンテンツ

      * `floating::Bool` - `badge` に対して、相対的に配置された親要素の右上に浮かぶべきかどうかを伝えます
      * `transparent::Bool` - 0.8 の不透明度を適用します; 特に浮かぶ `badge` に対して便利です
      * `multiline::Bool` - コンテンツが複数行に折り返すことができます
      * `label::Union{String, Int}` - バッジの内容を文字列として指定します; 指定された場合はデフォルトのスロットを上書きします ex. `"John Doe"` `22`
      * `align::String` - 垂直揃えの CSS 属性を設定します
      * `outline::Bool` - 'outline' デザイン（色付きのテキストと境界線のみ）を使用します
2. スタイル

      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette) からコンポーネントの色名 ex. `"primary"` `"teal-10"`
      * `textcolor::String` - テキストの色を上書きします（必要に応じて）; [カラーパレット](https://quasar.dev/style/color-palette) からの色名 ex. `"primary"` `"teal-10"`
      * `rounded::Bool` - 丸みを帯びた形のバッジを作成します
