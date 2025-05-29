```
keep!(data::PopData, kwargs...)
```

Edit a `PopData` object in-place by keeping only the occurrences of the specified keywords. If using multiple fields, they will be chained together as "`or`" statements. All values are converted to `String` for filtering, so `Symbol` and numbers will also work. This can be considered a simpler and more rudimentary syntax for subsetting  or filtering PopData.

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
keep!(cats, population = 1:5)

# keep 4 populations and 3 specific samples
keep!(cats, name = ["N100", "N102", "N211"])

# keep 2 loci, 2 populations, and 10 specific individuals
keep!(cats, locus = [:fca8, "fca37"], population = [7,8], name = samplenames(cats)[1:10])
```
