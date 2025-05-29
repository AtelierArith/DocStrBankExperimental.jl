```
toggle(label::Union{String,Symbol}, fieldname::Union{Symbol,Nothing}, args...; kwargs...)
```

`toggle`コンポーネントは、ユーザー入力のための基本的な要素の1つです。これを使用して、設定や機能、または真偽値の入力をオンまたはオフに切り替えることができます。

---

### 例

---

### モデル

```julia-repl
julia> @vars ToggleModel begin
          value::R{Bool} = false
          selection::R{Vector{String}} = ["yellow", "red"]
       end
```

### ビュー

```julia-repl
julia> toggle("Blue", color="blue", :selection, val="blue")
julia> toggle("Yellow", color="yellow", :selection, val="yellow")
julia> toggle("Green", color="green", :selection, val="green")
julia> toggle("Red", color="red", :selection, val="red")
```

---

### 引数

---

1. 挙動

      * `name::String` - コントロールの名前を指定するために使用されます; URLに直接送信されるフォームを扱う場合に便利です ex. `"car_id"`
      * `indeterminatevalue::Union{Int, Float64, String, Bool}` - どのモデル値を「不確定」と見なすべきですか？ デフォルト値: `null` ex. `0` `"not_answered"`
      * `toggleorder::String` - 2つの状態のトグル順序を決定します（'t'は真の状態、'f'は偽の状態を表します）； 'toggle-indeterminate'がtrueの場合、順序は: indet -> 最初の状態 -> 2番目の状態 -> indet（そして繰り返し）、そうでない場合: indet -> 最初の状態 -> 2番目の状態 -> 最初の状態 -> 2番目の状態 -> ... デフォルト `"tf"` ex. `"tf"` `"ft"`
      * `toggleindeterminate::Bool` - ユーザーがコンポーネントをクリック/タップしたとき、不確定状態も切り替えるべきですか？
      * `keepcolor::Bool` - コンポーネントが未チェック/オフのとき、色（指定されている場合）を保持すべきですか？
2. コンテンツ

      * `icon::String` - Quasarの規約に従ったアイコン名; 'img:'プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 'none'（String）が値として使用されると、アイコンは描画されません（ただし、画面の実際のスペースは依然として使用されます） ex. `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
      *
3. 一般

      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値 `0` `100`
4. アイコン

      * `checkedicon::String` - トグルがオンのときに使用されるアイコン ex. `visibility`
      * `uncheckedicon::String` - トグルがオフのときに使用されるアイコン ex. `visibility-off`
      * `indeterminateicon::String` - モデルが不確定のときに使用されるアイコン ex. `help`
5. ラベル

      * `label::Union{String,Symbol,Nothing}` - コンポーネントに表示されるラベル ex. `I agree to terms and conditions`
      * `leftlabel::Bool` - ラベル（指定されている場合）はコンポーネントの左側に表示されるべきです
6. モデル

      * `val::Union{Bool, Int, Float64, String, Vector}` - モデル（'value'）が配列のときに機能します。チェック/未チェックのときにどの値を追加/削除すべきかをコンポーネントに指示します ex. `car`
      * `truevalue::Union{Bool, Int, Float64, String, Vector}` - どのモデル値をチェック/チェック済み/オンと見なすべきですか？ デフォルト `true` ex. `Agreed`
      * `falsevalue::Union{Bool, Int, Float64, String, Vector}` - どのモデル値を未チェック/オフと見なすべきですか？ デフォルト `false` ex. `Not agreed`
7. 状態

      * `disabled::Bool` - コンポーネントを無効モードにします
8. スタイル

      * `size::String` - CSS単位でのサイズ、単位名または標準サイズ名（xs|sm|md|lg|xl）を含む ex. `16px` `1.5rem` `xs` `md`
      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名 ex. `primary` `teal-10`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `dense::Bool` - 密なモード; より少ないスペースを占有します
      * `iconcolor` - デフォルトのアイコン色をオーバーライドします（真の状態のみ）; [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名 ex. `primary` `teal-10`

```
