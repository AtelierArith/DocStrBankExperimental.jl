```
pairwisefst(data::PopData; method::Function, by::String = "global", iterations::Int64)
```

Calculate pairwise FST between populations in a `PopData` object. Set `iterations`  to a value greater than `0` to perform a single-tailed permutation test to obtain P-values of statistical significance. Use `by = "locus"` to perform a locus-by-locus FST for population pairs (iterations and significance testing ignored). Returns a `PairwiseFST` object, stores a `DataFrame` of the `results`, along with the `method` used to obtain the estimates. 

#### Methods:

  * `AMOVA`: AMOVA-based (Excoffier, 1992) FST as described by Bird et al. (2011) (default)
  * `Hudson`: Hudson et al. (1992) method (only for biallelic data)
  * `Nei`: Nei (1987) method
  * `WeirCockerham` : Weir & Cockerham (1984) method

**Examples**

```julia
data = @nancycats
wc = pairwise_fst(data, method = WeirCockerham)
wc_sig = pairwise_fst(data, iterations = 1000)
```
