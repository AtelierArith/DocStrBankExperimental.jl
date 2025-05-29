```
exclude!(data::PopData, kwargs...)
```

Edit a `PopData` object in-place by excluding all occurences of the specified information. The keywords can be used in any combination. Synonymous with `omit!` and `remove!`. All values are converted to `String` for filtering, so `Symbol` and numbers will also work. This can be considered a simpler and more rudimentary syntax for subsetting  or filtering PopData.

### Keyword Arguments

#### `locus`

A `String` or `Vector{String}` of loci you want to remove from the `PopData`. The keyword `loci` also works.

#### `population`

A `String` or `Vector{String}` of populations you want to remove from the `PopData` The keyword `populations` also works.

#### `name`

A `String` or `Vector{String}` of samples you want to remove from the `PopData` The keywords `names`, `sample`, and `samples` also work.

**Examples** ``` cats = @nancycats; exclude!(cats, name = "N100", population = 1:5) exclude!(cats, name = ["N100", "N102", "N211"], locus = ["fca8", "fca23"]) exclude!(cats, name = "N102", locus = :fca8, population = "3")
