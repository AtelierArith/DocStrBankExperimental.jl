```
keep(data::PopData, kwargs...)
```

Returns a new `PopData` object keeping only the occurrences of the specified keyword. Unlike `exclude()`. only one keyword can be used at a time. All values are  converted to `String` for filtering, so `Symbol` and numbers will also work. This can be considered a simpler and more rudimentary syntax for subsetting  or filtering PopData.

### Keyword Arguments

#### `locus`

A `String` or `Vector{String}` of loci you want to keep in the `PopData`.

#### `population`

A `String` or `Vector{String}` of populations you want to keep in the `PopData`.

#### `name`

A `String` or `Vector{String}` of samples you want to keep in the `PopData`.

**Examples**

```
cats = @nancycats;
keep(cats, population = 1:5)
# equivalent to cats[cats.genodata.population .∈ Ref(string.(1:5)), :]

keep(cats, name = ["N100", "N102", "N211"])
# equivalent to cats[cats.genodata.name .∈ Ref(["N100", "N102", "N211"]), :]

keep(cats, locus = [:fca8, "fca37"])
# equivalent to cats[cats.genodata.locus .∈ Ref(["fca8", "fca37"]), :]
```
