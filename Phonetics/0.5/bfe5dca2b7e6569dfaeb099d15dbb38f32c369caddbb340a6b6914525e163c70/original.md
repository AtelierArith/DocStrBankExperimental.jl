```
acdist(s1::Sound, s2::Sound, rep=:mfcc; [method=:dtw, dist=SqEuclidean(), radius=10])
```

Convert `s1` and `s2` to a frequency representation specified by `rep`, then calculate acoustic distance between `s1` and `s2`. Currently only `:mfcc` is supported for `rep`, using defaults from the `MFCC` package except that the first coefficient for each frame is removed and replaced with the sum of the log energy of the filterbank in that frame, as is standard in ASR.
