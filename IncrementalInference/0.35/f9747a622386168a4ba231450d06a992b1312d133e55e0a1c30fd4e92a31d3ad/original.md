```julia
printHistoryLane(fid, linecounter, hiVec)
printHistoryLane(fid, linecounter, hiVec, seqLookup)

```

Print one line of lanes summarizing all clique state machine histories.

Notes

  * hiVec is vector of all cliques (i.e. lanes) to print as one LINE into `fid` 

      * contains `::Tuple{Int,..}` with global counter (not the default CSM counter)
  * Vector of `CSMHistoryTuple`

Related:

printCliqHistoryLogical, printCliqHistoryLine
