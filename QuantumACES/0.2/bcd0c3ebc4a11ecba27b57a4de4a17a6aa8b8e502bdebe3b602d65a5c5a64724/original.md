```
apply!(t::Tableau, l::Layer; return_measurements::Bool = false)
```

Perform on the tableau `t` all gates in the layer `l`, and return the list of measurement outcomes if `return_measurements` is `true`.
