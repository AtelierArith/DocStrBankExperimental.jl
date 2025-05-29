```
  card(args...; kwargs...)
```

`Card` コンポーネントは、重要なグループ化されたコンテンツを表示するための優れた方法です。`Card` コンポーネントは意図的に軽量で、基本的には適切な他のコンポーネントを「ホスト」することができるコンテナ要素です。

---

### 例

---

### モデル

```julia-repl
julia> @vars CardModel begin
          lorem::R{String} = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
          url::R{String} = "https://cdn.quasar.dev/img/parallax2.jpg"
       end
```

### ビュー

```julia-repl
julia> card(class="my-card", [
          imageview(src=:url, no__transition=true, [
            Html.div("Title", class="absolute-bottom text-h6")
          ]),
          card_section("{{lorem}}")
       ])
```

---

### 引数

---

1. コンテンツ     * `tag::String` - デフォルトの `"div"` をレンダリングする HTML タグ ex. `"div"` `"form"`
2. スタイル     * `dark::Bool` - コンポーネントに背景が暗い色であることを通知     * `square::Bool` - ボーダー半径を削除し、ボーダーを直角にする     * `flat::Bool` - 'フラット' デザインを適用（デフォルトの影なし）     * `bordered::Bool` - コンポーネントにデフォルトのボーダーを適用

```
