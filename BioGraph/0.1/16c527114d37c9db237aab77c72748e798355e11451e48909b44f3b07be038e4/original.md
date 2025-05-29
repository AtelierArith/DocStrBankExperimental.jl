```
get_fasta(g_result::BioGraph.LongestPath; header::String="linear_path", outdir::String="")
```

Get FastA and Bed output of `LongestPath`. Will not generate files if `outdir` was not specified. 
