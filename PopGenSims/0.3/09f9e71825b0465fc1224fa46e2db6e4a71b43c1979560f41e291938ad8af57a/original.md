```
append!(data::PopData, data2::PopData)
```

Add the rows of `data2` to the end of `data`. This will add the samples present in the second `PopData` object to the first `PopData` object (mutating it).  **Note** that this is a simple appending, and you risk corrupting your `PopData` if the two `PopData` objects do not have identical loci.

**Example**

```
julia> cats = @nancycats
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 237
  Populations: 17

julia> purrfect_pairs = cross(cats, "N200", "N7", generation = "F1")
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 100
  Populations: 1

julia> append!(cats, purrfect_pairs);

julia> cats
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 337
  Populations: 18
```
