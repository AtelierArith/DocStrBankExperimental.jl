```
distinctiveness(s::Sound, corpus::Array{Sound}, rep=:mfcc; [method=:dtw, dist=SqEuclidean(), radius=10, reduction=mean])
```

Converts `s` and `corpus` to a representation specified by `rep`, then calculates the acoustic distinctiveness of `s` given `corpus`. Currently only `:mfcc` is supported for `rep`, using defaults from the `MFCC` package except that the first coefficient for each frame is removed and replaced with the sum of the log energy of the filterbank in that frame, as is standard in ASR.
