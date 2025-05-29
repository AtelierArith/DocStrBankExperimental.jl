```
featurematrix(data::PopData, matrixtype::Union{String, Symbol} = "genotype")
```

### Positional Arguments

```
- `data`: a PopData object
- `matrixtype`: a `String` or `Symbol` of `genotype`, or `allele` (default: `genotype`)
```

**genotype feature matrix**

Return a matrix of dummy-encoded genotypes (0,1,2...), where rows correspond with samples and columns correspond to loci. Missing genotypes are encoded as `-1`. For biallelic loci, `0` encodes homozygous for allele 1, `1` encodes for a heterozygote, and `2` encodes for homozygous allele 2.

**allele feature matrix**

Return a matrix of dummy-encoded alleles (0,1), where rows correspond with samples and columns correspond to alleles within loci, such that there are as many columns per locus as alleles for that locus. Missing alleles (from missing genotypes) are encoded as `-1`.

**Example**

```
julia> cats = @nancycats ;
julia> featurematrix(cats)
237×9 Matrix{Int8}:
 -1   0   0   0   0  0   0   0   0
 -1   1   1   1   0  0   1   0   0
  0   0   2   2   1  1   2   0   1
  1   2   3   3   2  0   0   1   0
  1   3   4   4   3  0   3   0   0
  ⋮                  ⋮
 49   0   1  -1  36  0   0  -1  13
 48   6   8  -1  25  1   2  -1   0
 29   9  23  -1   7  3  26  14   0
  3   5   8  -1   2  1   3  14   0
 29  10  16  -1   4  3   2  -1   0

 julia> featurematrix(cats, "allele")
237×108 Matrix{Int8}:
 -1  -1  -1  -1  -1  …  0  0  0  0  0  0
 -1  -1  -1  -1  -1     0  0  0  0  0  0
  0   0   0   0   0     0  0  0  0  0  0
  0   0   0   0   0     0  0  0  0  0  0
  0   0   0   0   0     0  0  0  0  0  0
  ⋮                  ⋱           ⋮
  0   0   0   0   0     0  0  0  1  0  0
  0   0   0   0   0     0  0  0  0  0  0
  0   0   0   0   0     0  0  0  0  0  0
  0   0   0   0   0  …  0  0  0  0  0  0
  0   0   0   0   0     0  0  0  0  0  0 
```
