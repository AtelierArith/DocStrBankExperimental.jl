```
xcorr(u,v; padmode = :none)
```

Compute the cross-correlation of two vectors, by calculating the similarity between `u` and `v` with various offsets of `v`. Delaying `u` relative to `v` will shift the result to the right.

The size of the output depends on the padmode keyword argument: with padmode = :none the length of the result will be length(u) + length(v) - 1, as with conv. With padmode = :longest the shorter of the arguments will be padded so they are equal length. This gives a result with length 2*max(length(u), length(v))-1, with the zero-lag condition at the center.
