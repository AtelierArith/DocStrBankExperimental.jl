---

### 例

---

```
card_actions()
```

### モデル

```julia-repl
julia> @vars CardModel begin
          lorem::R{String} = "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
       end
```

### ビュー

```julia-repl
julia> card(class="my-card bg-secondary text-white", [
          card_section([
            Html.div("私たちの変わりゆく地球", class="text-h6"),
            Html.div("ジョン・ドーによる", class="text-subtitle2")
          ]),
          card_section("{{ lorem }}"),
          card_actions([
            btn(flat=true, "アクション 1"),
            btn(flat=true, "アクション2")
          ])
        ])
```

---

### 引数

---

  * `align::String` - アクションの配置方法を指定します ("left", "center", "right", "between", "around", "evenly", "stretch")
  * `vertical:Bool` - アクションを一つずつ表示します
