```
Compose(; as=:coda)
```

Converts all columns of the table into parts of a composition in a new column named `as`, using the `CoDa.compose` function.

```
Compose(col₁, col₂, ..., colₙ; as=:coda)
Compose([col₁, col₂, ..., colₙ]; as=:coda)
Compose((col₁, col₂, ..., colₙ); as=:coda)
```

Converts the selected columns `col₁`, `col₂`, ..., `colₙ` into parts of a composition.

```
Compose(regex; as=:coda)
```

Converts the columns that match with `regex` into parts of a composition.

# Examples

```julia
Compose(as=:composition)
Compose([2, 3, 5])
Compose([:b, :c, :e])
Compose(("b", "c", "e"))
Compose(r"[bce]", as="composition")
```
