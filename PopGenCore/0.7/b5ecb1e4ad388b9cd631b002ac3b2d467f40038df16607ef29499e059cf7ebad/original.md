```
matrix(data::PopData, matrixtype::Union{String, Symbol} = "count", missings = "mean", scale = false, center = false)
```

Return a matrix of allele counts or frequencies per genotype where rows are samples and columns are the occurence count or frequency of an allele for that locus in that sample. Loci and alleles are sorted alphanumerically. Setting `scale` or `center` as `true` will compute allele frequencies regardless of the `by` keyword.

### Positional Arguments

  * `data`: a PopData object
  * `matrixtype`: a `String` or `Symbol` of `count` or `frequency` (default: `frequency`)

### Keyword Arguments

  * `missings`: a `String` denoting how to handle missing values when outputting `frequency` (default: `mean`)

      * `"missing"`: fallback method to keep `missing` values as they are
      * `"zero"`: replace `missing` values with `0`
      * `"mean"`: replace `missing` values with the mean frequency for that allele in that locus
  * `scale`: a 'Bool' of whether to z-score scale allele frequencies (default: `false`)
  * `center`: a `Bool` of whether to center the allele frequencies (default: 'false')

**Example**

```
julia> cats = @nancycats ;

julia> cnts = matrix(cats, "count") ;  cnts[1:5,1:6]
5×6 Matrix{Union{Missing, Int8}}:
  missing   missing   missing   missing   missing   missing
  missing   missing   missing   missing   missing   missing
 0         0         0         0         0         0
 0         0         0         0         0         0
 0         0         0         0         0         0

julia> frq = matrix(cats, "frequency") ;  frq[1:5,1:6]
5×6 Matrix{Union{Missing, Float32}}:
 0.00460829  0.00460829  0.0276498  0.133641  0.00460829  0.0921659
 0.00460829  0.00460829  0.0276498  0.133641  0.00460829  0.0921659
 0.0         0.0         0.0        0.0       0.0         0.0
 0.0         0.0         0.0        0.0       0.0         0.0
 0.0         0.0         0.0        0.0       0.0         0.0

 julia> frq = matrix(cats, :frequency, missings = "zero") ;  frq[1:5,1:6]
 5×6 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0

 julia> frq = matrix(cats, missings = "mean", scale = true, center = true) ;  frq[1:5,1:6]
 5×6 Matrix{Float32}:
  7.17017f-9   7.17017f-9   0.0        0.0        7.17017f-9   0.0
  7.17017f-9   7.17017f-9   0.0        0.0        7.17017f-9   0.0
 -0.0709577   -0.0709577   -0.175857  -0.394198  -0.0709577   -0.300797
 -0.0709577   -0.0709577   -0.175857  -0.394198  -0.0709577   -0.300797
 -0.0709577   -0.0709577   -0.175857  -0.394198  -0.0709577   -0.300797
```

```

```
