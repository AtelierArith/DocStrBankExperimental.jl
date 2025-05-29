```
radio(label::Union{String, Symbol, Nothing} = nothing, fieldname::Union{Symbol,Nothing} = nothing, args...; kwargs...)
```

`radio`コンポーネントは、ユーザー入力のための基本的な要素の1つです。これを使用して、ユーザーが複数の選択肢からオプションを選ぶ方法を提供できます。

---

### 例

---

### モデル

```julia-repl
julia> @vars RadioModel begin
         shape::R{String} = "line"
       end
```

### ビュー

```julia-repl
julia> radio("Line", :shape, val="line")
julia> radio("Rectangle", :shape, val="rectange")
julia> radio("Ellipse", :shape, val="ellipse")
julia> radio("Polygon", :shape, val="polygon")
```

---

### 引数

---

1. 挙動

      * `name::String` - コントロールの名前を指定するために使用されます; URLに直接送信されるフォームを扱う場合に便利です ex. `car_id`
      * `keep-color::Bool` - チェックボックスがオフのときに色（指定されている場合）を保持するべきですか？
2. 一般

      * `tabindex::Union{Int, String}` - タブインデックスHTML属性値
3. モデル

      * `fieldname::Symbol` - バインドする変数の名前。
4. ラベル

      * `label::AbstractString` - ラベル
      * `leftlabel::Bool` - ラベル（指定されている場合）はチェックボックスの左側に表示されるべきです
5. 状態

      * `disable::Bool` - コンポーネントを無効モードにする
6. スタイル

      * `size::String` - CSS単位でのサイズ、単位名または標準サイズ名（xs|sm|md|lg|xl）を含む ex. `16px` `2rem` `xs` `md`
      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名 ex. `primary` `teal-10`
      * `dark::Bool` - 背景が暗い色であることをコンポーネントに通知する
      * `dense::Bool` - 密なモード; より少ないスペースを占有する

```
