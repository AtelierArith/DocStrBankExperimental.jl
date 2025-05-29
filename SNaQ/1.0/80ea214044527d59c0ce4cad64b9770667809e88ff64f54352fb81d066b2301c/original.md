```
readnewicklevel1(filename)
readnewicklevel1(parenthetical format)
```

Similarly to [`PhyloNetworks.readnewick`](@extref): read a tree or network in parenthetical format, but this function enforces the necessary conditions for any starting topology in SNaQ: non-intersecting cycles, no polytomies, unrooted. It sets any missing branch length to 1.0, and reduces any branch length above 10 to 10 (as it assumes branch lengths are in coalescent units).

If the network has a bad diamond II (in which edge lengths are γ's are not identifiable) and if the edge below this diamond has a length `t` different from 0, then this length is set back to 0 and the major parent hybrid edge is lengthened by `t`.
