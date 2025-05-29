```
genotypes(data::PopData, samplelocus::String)
```

Return a vector of all the genotypes of a sample (or locus) in a `PopData` object.

```
cats = @nancycats
genotypes(cats, "N115")
genotypes(cats, "fca8")

```
