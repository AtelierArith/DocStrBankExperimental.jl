```
toolbar(args...; kwargs...)
```

`toolbar` is a component usually part of Layout Header and Footer, but it can be used anywhere on the page.

---

### Examples

---

### View

```julia-repl
julia> toolbar(class="text-primary", [
          btn(flat=true, round=true, dense=true, icon="menu"),
          toolbartitle("Toolbar"),
          btn(flat=true, round=true, dense=true, icon="more_vert")
       ])
```

---

### Arguments

---

  * `inset::Bool` - Apply an inset to content (useful for subsequent toolbars)
