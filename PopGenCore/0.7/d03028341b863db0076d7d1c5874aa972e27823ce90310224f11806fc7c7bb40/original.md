```
locusinfo!(::PopData, metadata::Pair{Symbol, Vector}; categorical::Bool = false)
locusinfo!(::PopData, metadata::Pair{String, Vector}; categorical::Bool = false)
```

Add an additional locus information to `PopData` metadata. Mutates `PopData` in place. Metadata  must be in the same order as the samples in `locusinfo(PopData)`.

#### Arguments

  * `metadata` : A Pair of :ColumnName => [Values]

#### Keyword Arguments

  * `categorical` : Boolean of whether the metadata being added is categorical aka "factors" (default: `false`)

## Example

```julia
cats = @nancycats
locusinfo!(cats, :quality => rand(metadata(cats).loci))
cats
PopData{Diploid, 9 Microsatellite loci}
  Samples: 237
  Populations: 17
  Other Info: ["quality"]
```
