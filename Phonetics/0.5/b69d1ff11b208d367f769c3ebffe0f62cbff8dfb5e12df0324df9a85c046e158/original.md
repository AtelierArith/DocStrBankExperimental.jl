```
avgseq(S::Array{Sound}, rep=:mfcc; [method=:dtw, dist=SqEuclidean(), radius=10, center=:medoid, dtwradius=nothing, progress=false])
```

Convert the `Sound` objects in `S` to a representation designated by `rep`, then find the average sequence of them. Currently only `:mfcc` is supported for `rep`, using defaults from the `MFCC` package except that the first coefficient for each frame is removed and replaced with the sum of the log energy of the filterbank in that frame, as is standard in ASR.
