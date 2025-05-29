```julia
printCSMHistoryLogical(hists; ...)
printCSMHistoryLogical(hists, fid; order, printLines)

```

Print history in swimming lanes, side by side with global sequence counter.

Examples

```julia
printCSMHistoryLogical(hist)
printCSMHistoryLogical(hists, order=[4;3], printLines=2:5)

# or to a IOStream, file, network, etc
fid = open(joinLogPath(fg, "CSMHistCustom.txt"),"w")
printCSMHistoryLogical(hist, fid)
close(fid)
```

DevNotes

  * `order` should be flexible like `Sequential` and `<:CSMRanges`.
