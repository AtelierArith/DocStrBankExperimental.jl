```
form(args...; noresetfocus::Bool = false, kwargs...)
```

`form` コンポーネントは <form> DOM 要素をレンダリングし、内部バリデーション（外部バリデーションではない）を持つ子フォームコンポーネント（`input`、`select` または `field` でラップされたコンポーネントなど）を簡単に検証できるようにします。

---

### 例

---

### モデル

```julia-repl
julia> @vars FormModel begin
          name::R{String} = ""
          age::R{Int} = 0
          warin::R{Bool} = true
       end
```

### ビュー

```julia-repl
julia> StippleUI.form(action = "/sub", method = "POST", [
          textfield("あなたの名前は何ですか *", :name, name = "name", @if(:warin), :filled, hint = "名前と姓", "lazy-rules",
            rules = "[val => val && val.length > 0 || '何かを入力してください']"
          ),
          numberfield("あなたの年齢 *", :age, name = "age", "filled", :lazy__rules,
            rules = "[val => val !== null && val !== '' || 'あなたの年齢を入力してください',
              val => val > 0 && val < 100 || '実際の年齢を入力してください']"
          ),
          btn("送信", type = "submit", color = "primary")
       ])
```

---

### 引数

---

  * `autofocus::Bool` - 初期コンポーネントレンダリング時に最初のフォーカス可能な要素にフォーカスを当てる
  * `noerrorfocus::Bool` - フォームを送信する際にバリデーションエラーがある最初のコンポーネントにフォーカスを当てようとしない
  * `noresetfocus::Bool` - フォームをリセットする際に最初のコンポーネントにフォーカスを当てようとしない
  * `greedy::Bool` - フォーム内のすべてのフィールドを検証する（デフォルトでは、同期バリデーションで最初の無効なフィールドを見つけた後に停止します）
