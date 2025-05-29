```
run_gemma(dataset::String,trait::String; use_loco::Bool=false, maf::Float64=0.01,
    gn_url::String=gn_url())
```

Runs GEMMA with the specified `trait` in the specified `dataset`. Optional arguments include:

  * use_loco (default=false): if LOCO (leave one chromosome out) should be used
  * maf (default=0.01): the minimum minor allele frequency of the markers to be scanned
