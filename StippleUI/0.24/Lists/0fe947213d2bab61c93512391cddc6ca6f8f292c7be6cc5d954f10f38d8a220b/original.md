```
  list(args...; kwargs...)
```

The `list` and `item` are a group of components which can work together to present multiple line items vertically as a single continuous element. They are best suited for displaying similar data types as rows of information, such as a contact list, a playlist or menu. Each row is called an Item. `item` can also be used outside of a `list` too.

---

### Examples

---

### View

```julia-repl
julia>  list(bordered=true, separator=true, [
          item(clickable=true, vripple=true, [
            itemsection("Single line item")
          ]),

          item(clickable=true, vripple=true, [
            itemsection([
              itemlabel("Item with caption"),
              itemlabel("Caption", caption=true)
            ])
          ]),

          item(clickable=true, vripple=true, [
            itemsection([
              itemlabel("OVERLINE", overline=true),
              itemlabel("Item with caption")
            ])
          ])
        ])
```

---

### Arguments

---

1. Content

      * `separator::Bool` - Applies a separator between contained items
      * `padding:Bool` - Applies a material design-like padding on top and bottom
2. Style

      * `bordered::Bool` - Applies a default border to the component
      * `dense::Bool` - Dense mode; occupies less space
      * `dark::Bool` - Notify the component that the background is a dark color
