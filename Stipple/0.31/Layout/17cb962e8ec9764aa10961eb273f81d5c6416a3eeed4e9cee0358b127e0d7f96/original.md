```
add_css(css::Function; update = true)
```

Add a css function to the `THEMES[]`.

### Params

  * `css::Function` - a function that results in a vector of style elements
  * `update` - determines, whether existing style sheets with the same name shall be removed

### Example

```julia
# css to remove the stipple-core color format of q-table rows
# (this will enable font color setting by the attribute `table-class`)

function mycss()
  [
    style("""
    .stipple-core .q-table tbody tr { color: inherit; }
    """)
  ]
end

add_css(mycss)
```

`
