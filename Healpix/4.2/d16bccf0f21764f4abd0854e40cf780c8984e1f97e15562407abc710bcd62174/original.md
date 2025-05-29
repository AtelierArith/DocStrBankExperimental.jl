```
queryStripRing(resol::Resolution, theta1, theta2; inclusive=true)
```

Return a range of the indices of pixels that overlap with the colatitude range `[theta1, theta2]`. If `inclusive` is set to `false`, only those pixels whose *centers* lie within the colatitude range are returned.

This function assumes the RING scheme, because in this case, the indexes of the pixels cover a range without gaps. Therefore, the function returns a *range* instead of a *list*, as it is quicker and occupies far less memory.
