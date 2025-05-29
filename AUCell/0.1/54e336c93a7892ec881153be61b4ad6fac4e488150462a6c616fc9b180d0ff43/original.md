```
read_mtx(fn, rn, cn)
```

Read in the common 10X single-cell RNA expression file in the MTX format (unzipped).

# Examples

```jldoctest
julia> @time mat, fea, bar = read_mtx("matrix.mtx", "features.tsv", "barcodes.tsv")
 62.946154 seconds (481.84 M allocations: 13.082 GiB, 3.50% gc time)
(sparse([7, 27, 31, 44, 45, 46, 49, 52, 54, 58  …  36563, 36564, 36565, 36566, 36567, 36568, 36569, 36570, 36572, 36576], [1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  5744, 5744, 5744, 5744, 5744, 5744, 5744, 5744, 5744, 5744], Int32[1, 1, 5, 1, 4, 1, 1, 1, 1, 1  …  287, 8, 239, 124, 32, 8, 145, 41, 99, 2], 36601, 5744), Any["ENSG00000243485", "ENSG00000237613", "ENSG00000186092", "ENSG00000238009", "ENSG00000239945", "ENSG00000239906", "ENSG00000241860", "ENSG00000241599", "ENSG00000286448", "ENSG00000236601"  …  "ENSG00000274175", "ENSG00000275869", "ENSG00000273554", "ENSG00000278782", "ENSG00000277761", "ENSG00000277836", "ENSG00000278633", "ENSG00000276017", "ENSG00000278817", "ENSG00000277196"], Any["AAACCCAAGAACAAGG-1", "AAACCCAAGCCTGAAG-1", "AAACCCAAGCTGAGTG-1", "AAACCCAAGTATTGCC-1", "AAACCCAGTCATGACT-1", "AAACCCATCGGAATTC-1", "AAACCCATCTGTCTCG-1", "AAACGAAAGCGGGTAT-1", "AAACGAAAGGTAGCCA-1", "AAACGAAAGTGGTGAC-1"  …  "TTTGGTTTCCACAGCG-1", "TTTGTTGCACCTCGTT-1", "TTTGTTGCAGCTGTTA-1", "TTTGTTGCATACCGTA-1", "TTTGTTGGTAGGACCA-1", "TTTGTTGGTGACAGGT-1", "TTTGTTGTCCACTTTA-1", "TTTGTTGTCCTATTGT-1", "TTTGTTGTCGCTCTAC-1", "TTTGTTGTCTCCAAGA-1"])

```

# Arguments

  * `fn::AbstractString`: MTX file path .
  * `rn::AbstractString`: features file path.
  * `cn::AbstractString`: barcodes file path.
  * `T::Type`: Datatype in the MTX file. Default: Int32.
  * `feature_col::Int`: which column is used as feature names. Default: 1 (first).
  * `barcode_col::Int`: which column is used as barcode names. Default: 1 (first).
