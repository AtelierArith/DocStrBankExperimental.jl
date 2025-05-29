function troendle(perm::AbstractMatrix,stat::AbstractVector;type=:twosided)

Multiple Comparison Correction as in Troendle 1995

`perm` with size  ntests x nperms

`stat` with size ntests

`type` can be :twosided (default), :lesser, :greater

Heavily inspired by the R implementation in permuco from Jaromil Frossard

Note: While permuco is released under BSD, the author Jaromil Frossard gave us an MIT license for the troendle and the clusterdepth R-functions.
