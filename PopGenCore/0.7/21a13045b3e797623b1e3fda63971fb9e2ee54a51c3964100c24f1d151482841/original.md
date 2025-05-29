```
exclude(data::PopData, kwargs...)
```

Returns a new `PopData` object excluding all occurrences of the specified keywords. The keywords can be used in any combination. Synonymous with `omit` and `remove`. All values are converted to `String` for filtering, so `Symbol` and numbers will also work. This can be considered a simpler and more rudimentary syntax for subsetting  or filtering PopData.

### Keyword Arguments

#### `locus`

A `String` or `Vector{String}` of loci you want to remove from the `PopData`.

#### `population`

A `String` or `Vector{String}` of populations you want to remove from the `PopData`.

#### `name`

A `String` or `Vector{String}` of samples you want to remove from the `PopData`.

**Examples**

```
cats = @nancycats;
exclude(cats, name = "N100", population = 1:5)
exclude(cats, name = ["N100", "N102", "N211"], locus = ["fca8", "fca23"])
exclude(cats, name = "N102", locus = :fca8, population = "3")
```
