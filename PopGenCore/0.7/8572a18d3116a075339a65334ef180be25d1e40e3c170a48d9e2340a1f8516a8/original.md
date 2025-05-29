```
delimited(data::PopData; filename::String, delim::String = ",", digits::Integer = 3, format::String = "wide", miss::Int = 0)
```

Write PopData to a text-delimited file.

### Keyword Arguments

  * `filename`: a `String` of the output filename
  * `digits` : an `Integer` indicating how many digits to format each allele as (e.g. `(1, 2)` => `001002` for `digits = 3`)
  * `format` : a `String` indicating whether to output in`"wide"` or `"long"` (aka `"tidy"`) format

      * `wide` : the standard format CSV for importing into PopGen.jl
      * `long` : the `loci` table with `longitude` and `latitude` columns added
  * `delim` : the `String` delimiter to use for writing the file
  * `miss` : an `Integer` for how you would like missing values written 

      * `0` : As a genotype represented as a number of zeroes equal to `digits × ploidy` like `000000` (default)
      * `-9` : As a single value `-9`

### Example

```julia
cats = @nancycats;
fewer_cats = omit(cats, name = samplenames(cats)[1:10]);
delimited(fewer_cats, filename = "filtered_nancycats.gen", digits = 3, format = "wide", delim = " ")
```
