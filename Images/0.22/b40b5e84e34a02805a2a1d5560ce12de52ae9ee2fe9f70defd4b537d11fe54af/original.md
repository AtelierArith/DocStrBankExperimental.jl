```
fastcorners(img, n, threshold) -> corners
```

Performs FAST Corner Detection. `n` is the number of contiguous pixels which need to be greater (lesser) than intensity + threshold (intensity - threshold) for a pixel to be marked as a corner. The default value for n is 12.
