```
Column(name::String, args...)
```

---

### Examples

---

```julia-repl
julia> Column("x2", align = :right)
```

---

### Arguments

---

  * `required::Bool` - if we use `visiblecolumns`, this col will always be visible
  * `label::String` - label for header
  * `align::Symbol` - alignment for cell
  * `field::String` - row Object property to determine value for this column ex. `name`
  * `sortable::Bool` - tell `table` you want this column sortable
