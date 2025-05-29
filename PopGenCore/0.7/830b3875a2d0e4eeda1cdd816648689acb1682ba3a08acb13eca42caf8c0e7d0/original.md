```
locimatrix(data::PopData)
```

Return a matrix of genotypes with dimensions `samples × loci`. Rows are samples and columns are loci. Will return an error if ploidy varies between samples. 

**Example**

```julia
julia> locimatrix(@nancycats)
237×9 Matrix{Union{Missing, Tuple{Int16, Int16}}}:
 missing     …  (208, 208)
 missing        (208, 208)
 (135, 143)     (210, 210)
 (133, 135)     (208, 208)
 (133, 135)     (208, 208)
 (135, 143)  …  (208, 208)
 ⋮           ⋱
 (133, 141)     (208, 220)
 (133, 143)     (208, 208)
 (135, 141)     (208, 208)
 (137, 143)  …  (208, 208)
 (135, 141)     (208, 208)
```
