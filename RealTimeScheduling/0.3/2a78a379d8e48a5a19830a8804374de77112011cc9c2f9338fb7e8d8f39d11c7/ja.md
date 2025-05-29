```
completed(j::AbstractJob)
```

ジョブ `j` が完了したかどうかを返します。すなわち、`exectime(j) >= cost(j)` であるかどうかです。
