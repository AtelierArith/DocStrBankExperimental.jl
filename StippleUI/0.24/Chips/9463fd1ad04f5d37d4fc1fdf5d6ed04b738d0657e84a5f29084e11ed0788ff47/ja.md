```
  chip(args...; kwargs...)
```

`chip` コンポーネントは基本的にシンプルな UI ブロックエンティティで、例えば連絡先のようなより高度な基盤データをコンパクトに表現します。

チップにはアバター、テキスト、アイコンなどのエンティティを含めることができ、オプションでポインターも持つことができます。また、設定に応じて閉じたり削除したりすることも可能です。

---

### 例

---

### 表示

```julia-repl
julia> chip("カレンダーに追加", icon="event")
```

---

### 引数

---

1. コンテンツ

      * `icon::String` - Quasar 規約に従ったアイコン名; 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 'none' (String) が値として使用されると、アイコンは描画されません（ただし、画面の不動産は依然としてそれに使用されます）例: `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `iconright::String` - Quasar 規約に従ったアイコン名; 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 'none' (String) が値として使用されると、アイコンは描画されません（ただし、画面の不動産は依然としてそれに使用されます）例: `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `iconremove::String` - Quasar 規約に従ったアイコン名; 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 'none' (String) が値として使用されると、アイコンは描画されません（ただし、画面の不動産は依然としてそれに使用されます）例: `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `iconselected::String` - Quasar 規約に従ったアイコン名; 'img:' プレフィックスを使用しない限り、アイコンライブラリがインストールされていることを確認してください; 'none' (String) が値として使用されると、アイコンは描画されません（ただし、画面の不動産は依然としてそれに使用されます）例: `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `label::Union{String, Int}` - チップの内容を文字列として; 指定された場合はデフォルトスロットをオーバーライドします例: `"Joe Doe"` `"Book"`
2. 一般

      * `tabindex::Union{Int, String}` - タブインデックス HTML 属性値例: `0` `100`
3. モデル

      * `value::Bool` - `chip` が描画されるかどうかを決定するコンポーネントのモデル。デフォルトは `true`
      * `selected::Bool` - `chip` が選択されているかどうかのモデル。モデルプロパティに設定する必要があります。
4. 状態

      * `clickable::Bool` - `chip` はクリック可能ですか？その場合、ホバー効果が追加され、'click' イベントが発生します
      * `removable::Bool` - `chip` は削除可能ですか？その場合、閉じるボタンが追加され、'remove' イベントが発生します
      * `disable::Bool` - コンポーネントを無効モードにします
5. スタイル

      * `ripple::Union{Bool, Dict}` - マテリアルリップルを設定します（'false' に設定することで無効にするか、設定オブジェクトを提供します）デフォルトは `true` 例: `false` `{ early: true, center: true, color: 'teal', keyCodes: [] }`
      * `dense::Bool` - 密なモード; より少ないスペースを占有します
      * `size::String` - `chip` サイズ名または単位名を含む CSS 単位例: `"xs"` `"sm"` `"md"` `"lg"` `"xl"` `"1rem"`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `color::String` - コンポーネントの色名 [カラーパレット](https://quasar.dev/style/color-palette) から例: `"primary"` `"teal-10"`
      * `square::Bool` - デフォルトの値の代わりに低い値をボーダー半径に設定し、四角に近づけます
      * `outline::Bool` - 'outline' デザインを使用して表示します

```
