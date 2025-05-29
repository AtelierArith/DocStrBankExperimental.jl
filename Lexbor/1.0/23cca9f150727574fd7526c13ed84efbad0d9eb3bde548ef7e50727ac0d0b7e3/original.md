```
is_element(node::Node) -> Bool
```

Is the `node` an HTML element `Node`? E.g. a `<a>`, `<div>`, etc.

Use [`tag`](@ref Lexbor.tag) to access the name of the element as a `Symbol` and use [`attributes`](@ref Lexbor.attributes) to access the element attributes.
