```
genepop(data::PopData; filename::String = "output.gen", digits::Int = 3, format::String = "vertical", miss::Int = 0)
```

Writes a `PopData` object to a Genepop-formatted file.

  * `data`: the `PopData` object you wish to convert to a Genepop file

### keyword arguments

  * `filename`: a `String` of the output filename
  * `digits` : an `Integer` indicating how many digits to format each allele as (e.g. `(1, 2)` => `001002` for `digits = 3`)
  * `format` : a `String` indicating whether loci should be formatted

      * vertically (`"v"` or `"vertical"`)
      * hortizontally (`"h"`, or `"horizontal"`)
      * Genepop Isolation-By-Distance (`"ibd"`) where each sample is a population with long/lat data prepended
  * `miss` : an `Integer` for how you would like missing values written 

      * `0` : As a genotype represented as a number of zeroes equal to `digits × ploidy` like `000000` (default)
      * `-9` : As a single value `-9`

## Example

```julia
cats = @nancycats;
fewer_cats = omit(cats, name = samplenames(cats)[1:10]);
genepop(fewer_cats, filename = "filtered_nancycats.gen", digits = 3, format = "h")
```
