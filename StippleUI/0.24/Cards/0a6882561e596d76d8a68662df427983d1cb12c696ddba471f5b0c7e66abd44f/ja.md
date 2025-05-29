```
  card_section(args...; kwargs...)
```

---

### 例

---

### 表示

```julia-repl
julia> card(class="text-white", style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%); width: 30%", [
          card_section("lorLorem Ipsum is simply dummy text of the printing
          and typesetting industry")
       ])
```

---

### 引数

---

  * `tag::String` - レンダリングするHTMLタグ 例: `"div"`, `"form"`
  * `horizontal::Bool` - 水平セクションを表示する（パディングはなく、他の`card_section`を含むことができます）
