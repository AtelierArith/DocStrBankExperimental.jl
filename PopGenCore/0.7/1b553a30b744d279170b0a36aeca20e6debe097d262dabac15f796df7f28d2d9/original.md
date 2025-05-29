```
genotypes(data::PopData, samplelocus::Pair{String, String}) ::DataFrame
genotypes(data::PopData, samplelocus::Pair{Vector{String}, String}) ::DataFrame
genotypes(data::PopData, samplelocus::Pair{String, Vector{String}}) ::DataFrame
```

Return a genotype or dataframe of genotypes for one or more samples/loci  in a `PopData` object. Uses the `Pair` notation of `samples => loci`.

### Examples

```
cats = @nancycats;
genotypes(cats, "N115" => "fca8")
genotypes(cats, ["N115", "N7"] => "fca8")
genotypes(cats, "N115" => ["fca8", "fca37"])
genotypes(cats, ["N1", "N2"] => ["fca8", "fca37"])
```
