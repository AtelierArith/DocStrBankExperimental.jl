```
describe(geotable)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; skipmissing=true)
```

Return descriptive table of all `geotable` columns using the descriptive  functions `fun₁`, `fun₂`, ..., `funₙ`, and skipping or not the missing values using the `skipmissing` keyword argument. Optionally, define a `nameᵢ` to `funᵢ` by passing a pair. If the descriptive functions are not passed, the default functions will be used, they are: `mean`, `minimum`, `median`, `maximum`, `nmissing`.

```
describe(geotable; cols=[col₁, col₂, ..., colₙ])
describe(geotable; cols=(col₁, col₂, ..., colₙ))
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=[col₁, col₂, ..., colₙ], skipmissing=true)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=(col₁, col₂, ..., colₙ), skipmissing=true)
```

Return descriptive table of columns `col₁`, `col₂`, ..., `colₙ`.

```
describe(geotable; cols=regex)
describe(geotable; cols=regex)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=regex, skipmissing=true)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=regex, skipmissing=true)
```

Return descriptive table of columns that match with `regex`.

# Examples

```julia
describe(geotable)
describe(geotable, mean, median)
describe(geotable, std, var, cols=(1, 3, 5))
describe(geotable, maximum, minimum, cols=[:a, :c, :e])
describe(geotable, :min => minimum, first, last, cols=("a", "c", "e"))
describe(geotable, :min => minimum, :max => maximum, cols=r"[ace]", skipmissing=false)
```
