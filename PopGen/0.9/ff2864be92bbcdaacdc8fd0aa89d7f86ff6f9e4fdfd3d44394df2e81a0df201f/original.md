```
heterozygosity(data::PopData; by::Union{Symbol,String} = "locus")
```

Calculate observed and expected heterozygosity in a `PopData` object. For loci, heterozygosity is calculated in the Nei fashion, such that heterozygosity is calculated as the average over heterozygosity per locus per population.

### Modes

  * `"locus"` : heterozygosity per locus (default)
  * `"sample"` : heterozygosity per individual/sample
  * `"population"`: heterozygosity per population

## Example

heterozygosity(@nancycats, by = "population" )
