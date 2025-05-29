```
  tab(args...; kwargs...)
```

`tabs` は、より少ないウィンドウスペースを使用してより多くの情報を表示する方法です。

---

### 例

---

### 表示

```julia-repl
julia> tab(name="photos", icon="photos", label="Photos")
```

---

### 引数

---

1. コンテンツ

      * `icon::String` - Quasarの規約に従ったアイコン名; 'img:' プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 'none' (String) が値として使用されると、アイコンは表示されません（ただし、画面スペースは依然として使用されます）。例。 `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `label::Union{Int,String}` - タブにラベルを付けるための数値または文字列。例。 `"Home"`
      * `alert::Union{Bool,String}` - タブにアラートシンボルを追加し、ユーザーに更新があることを通知します; 値がBooleanでない場合、色を指定できます。例。 `"alert"`
      * `nocaps::Bool` - タブ内のすべての文字を大文字にするのをオフにします（これがデフォルトです）
2. 一般

      * `name::Union{Int,String}` - パネル名。例。 `"home"` `name! ="1"`
      * `tabindex::Union{Int,String}` - Tabindex HTML属性値。例。 `0` `100`
3. 状態

      * `disable::Bool` - コンポーネントを無効モードにします
4. スタイル

      * `ripple::Union{Bool,Dict}` - マテリアルリップルを設定します（'false'に設定することで無効にするか、設定オブジェクトを提供します）。例。 `false` `"""{"early" => true, "center" => true, "color" => "teal", "keyCodes" => []}"""`
      * `contentclass::String` - コンテンツラッパーに属性を付与するクラス定義。 `"my-special-class"`

```
