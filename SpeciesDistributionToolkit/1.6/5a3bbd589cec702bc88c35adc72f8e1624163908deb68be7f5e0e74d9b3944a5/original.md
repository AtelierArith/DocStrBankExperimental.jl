```
gainloss(contemporary::SDMLayer{Bool}, future::SDMLayer{Bool})
```

Returns a layer with values -1, 0, and 1 corresponding to the difference in ranges. The two layers given as input must be layers with boolean values where `true` indicates that the pixel is in the range. The presence of `false` pixels is irrelevant as these are ignored internally.
