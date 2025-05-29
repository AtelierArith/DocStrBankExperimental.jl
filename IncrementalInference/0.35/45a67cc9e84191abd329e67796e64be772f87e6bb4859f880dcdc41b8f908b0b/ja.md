```julia
printCSMHistoryLogical(hists; ...)
printCSMHistoryLogical(hists, fid; order, printLines)

```

履歴をスイミングレーンで印刷し、グローバルシーケンスカウンタと並べて表示します。

例

```julia
printCSMHistoryLogical(hist)
printCSMHistoryLogical(hists, order=[4;3], printLines=2:5)

# または IOStream、ファイル、ネットワークなどに
fid = open(joinLogPath(fg, "CSMHistCustom.txt"),"w")
printCSMHistoryLogical(hist, fid)
close(fid)
```

DevNotes

  * `order` は `Sequential` や `<:CSMRanges` のように柔軟であるべきです。
