# Examples

## default: reAUCluster mode

```jldoctest
julia> pathway_AUC_main(use_testdata = "yes")
1.632442 seconds (8.44 M allocations: 279.642 MiB, 7.95% gc time, 73.87% compilation time)
[ Info: INFO: The size of expression profile was (36602, 8).
1.779532 seconds (4.95 M allocations: 260.557 MiB, 4.14% gc time, 97.91% compilation time)
[ Info: INFO: The filtered of expression profile size was (7549, 8).
0.000320 seconds (27 allocations: 34.672 KiB)
[ Info: INFO: There are 1 pathways to be analyzed.
0.768511 seconds (1.50 M allocations: 99.943 MiB, 2.46% gc time, 95.16% compilation time)
2×5 Matrix{Any}:
"pathways_name"                     ["cluster1"]                                                                                                       …  ["t"]      ["pvalue"]
"HALLMARK_TNFA_SIGNALING_VIA_NFKB"  Any["AAACCCAAGGGTTAAT-1", "AAACCCAAGAAACCAT-1", "AAACCCAAGCAACAAT-1", "AAACCCAAGCCAGAGT-1", "AAACCCACAGCAGATG-1"]     [4.92654]  [0.00263937]
```

## aucell mode

```jldoctest
julia> pathway_AUC_main(use_testdata = "yes", mode = "aucell")
  1.557316 seconds (8.44 M allocations: 279.659 MiB, 3.27% gc time, 78.85% compilation time)
[ Info: INFO: The size of expression profile was (36602, 8).
  1.771720 seconds (4.95 M allocations: 260.557 MiB, 3.69% gc time, 97.39% compilation time)
[ Info: INFO: The filtered of expression profile size was (7549, 8).
  0.000329 seconds (27 allocations: 34.672 KiB)
[ Info: INFO: There are 1 pathways to be analyzed.
  0.667055 seconds (1.75 M allocations: 87.598 MiB, 3.82% gc time, 99.79% compilation time)
[ Info: INFO: According to the meta information, there are 8 groups of data and each group will be analyzed with the rest of the sample.
  3.153389 seconds (6.62 M allocations: 421.960 MiB, 3.39% gc time, 80.62% compilation time)
2×65 Matrix{Any}:
 "GeneSet"                            "AAACCCAAGAAACCAT-1"   "AAACCCAAGAAACCAT-1"   "AAACCCAAGAAACCAT-1"  …   "AAACCCAGTACGGGAT-1"   "AAACCCAGTACGGGAT-1"   "AAACCCAGTACGGGAT-1"
 "HALLMARK_TNFA_SIGNALING_VIA_NFKB"  0.506962               0.500821               0.515332                  0.512858               0.482078               0.440029
```
