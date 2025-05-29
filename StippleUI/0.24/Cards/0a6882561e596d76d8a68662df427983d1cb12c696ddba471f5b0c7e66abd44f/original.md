```
  card_section(args...; kwargs...)
```

---

### Examples

---

### View

```julia-repl
julia> card(class="text-white", style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%); width: 30%", [
          card_section("lorLorem Ipsum is simply dummy text of the printing
          and typesetting industry")
       ])
```

---

### Arguments

---

  * `tag::String` - HTML tag to render ex. `"div"`, `"form"`
  * `horizontal::Bool` - Display a horizontal section (will have no padding and can contain other `card_section`)
