```
sampleinfo!(::PopData, metadata::Pair{Symbol, Vector}; categorical::Bool = false)
sampleinfo!(::PopData, metadata::Pair{String, Vector}; categorical::Bool = false)
```

Add an additional sample information to `PopData` metadata. Mutates `PopData` in place. Metadata  must be in the same order as the samples in `sampleinfo(popdata)`.

#### Arguments

  * `metadata` : A Pair of :ColumnName => [Values]

#### Keyword Arguments

  * `categorical` : Boolean of whether the metadata being added is categorical aka "factors" (default: `false`)

## Example

```julia
cats = @nancycats
sampleinfo!(cats, :whiskerlength => rand(cats.metadata.samples))
sampleinfo!(cats, "tailcolor" => rand(["orange", "brown"], metadata(cats).samples), categorical = true)
cats
PopData{Diploid, 9 Microsatellite loci}
  Samples: 237
  Populations: 17
  Other Info: ["whiskerlength", "tailcolor"]
```
