```
  checkbox(label::Union{String,Symbol} = "", fieldname::Union{Symbol,Nothing} = nothing, args...; kwargs...)
```

`checkbox` コンポーネントは、ユーザー入力のための基本的な要素の一つです。これを使用して、ユーザーがオプションを切り替える方法を提供できます。

---

### 例

---

### モデル

```julia-repl
julia> @vars CheckboxModel begin
          valone::R{Bool} = true
       end
```

### ビュー

```julia-repl
julia> checkbox(label = "Apples", fieldname = :valone, dense = true, size = "xl")
```

---

### 引数

---

1. 動作

      * `name::String` - コントロールの名前を指定するために使用されます; URL に直接送信されるフォームを扱う場合に便利です
      * `indeterminatevalue::Union{String, Float64, Int, Bool}` - どのモデル値が「不確定」と見なされるべきですか？
      * `toggleorder::String` - 2つの状態のトグル順序を決定します（'t' は真の状態、'f' は偽の状態を表します）； 'toggle-indeterminate' が true の場合、順序は: indet -> 最初の状態 -> 2番目の状態 -> indet（そして繰り返し）、そうでない場合: indet -> 最初の状態 -> 2番目の状態 -> 最初の状態 -> 2番目の状態 -> ... 例: `"tf"` `"ft"`
      * `toggleindeterminate::Bool` - ユーザーがコンポーネントをクリック/タップしたとき、不確定状態も切り替えるべきですか？
      * `keepcolor::Bool` - コンポーネントが未チェック/オフのとき、色（指定されている場合）を保持すべきですか？
2. 一般

      * `tabindex::Union{Int, String}` - タブインデックス HTML 属性値
3. ラベル

      * `label::Union{String,Symbol}` - コンポーネントに沿って表示するラベル
      * `leftlabel::Bool` - ラベル（指定されている場合）はコンポーネントの左側に表示されるべきです
4. モデル

      * `fieldname::Symbol` - コンポーネントのモデル
      * `val::Union{String, Float64, Int, Bool}` - モデル（'value'）が配列のときに機能します。チェック/未チェックのときにどの値を追加/削除すべきかをコンポーネントに指示します
      * `truevalue::Union{Int, Float64, String}` - どのモデル値がチェック/チェック済み/オンと見なされるべきですか？
      * `falsevalue::Union{Int, Float64, String}` - どのモデル値が未チェック/未チェック済み/オフと見なされるべきですか？
5. 状態

      * `disable::Bool` - コンポーネントを無効モードにします
6. スタイル

      * `size::String`- CSS 単位でのサイズ、単位名または標準サイズ名（xs|sm|md|lg|xl）を含む例: `"16px"` `"2rem"` `"xs"` `"md"`
      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette) からコンポーネントの色名例: `"primary"` `"teal-10"`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `dense::Bool` - 密なモード; より少ないスペースを占有します
