```
toolbar(args...; kwargs...)
```

`toolbar`は通常、レイアウトのヘッダーとフッターの一部として使用されるコンポーネントですが、ページのどこにでも使用できます。

---

### 例

---

### 表示

```julia-repl
julia> toolbar(class="text-primary", [
          btn(flat=true, round=true, dense=true, icon="menu"),
          toolbartitle("Toolbar"),
          btn(flat=true, round=true, dense=true, icon="more_vert")
       ])
```

---

### 引数

---

  * `inset::Bool` - コンテンツにインセットを適用します（後続のツールバーに便利です）
