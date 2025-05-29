```
Material(shelf, book, page) -> Union{Material, Vector{Material}}
```

Provide the *shelf*, *book* and *page* of the material separately. This method then calls `Material("$shelf/$book/$page")`.

# Arguments

  * `shelf::String` : The shelf of the material
  * `book::String` : The book of the material
  * `page::String` : The page of the material
