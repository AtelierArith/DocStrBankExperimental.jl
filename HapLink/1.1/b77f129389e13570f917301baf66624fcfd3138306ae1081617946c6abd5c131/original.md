```
variation_test(depth::Int, altdepth::Int, quality::Float64)
```

Conducts a Fisher's Exact Test to deterimine the likelihood of a variant with total `depth` and variation depth `altdepth` occuring, given an average basecall `quality`. Returns the $p$-value of the test.
