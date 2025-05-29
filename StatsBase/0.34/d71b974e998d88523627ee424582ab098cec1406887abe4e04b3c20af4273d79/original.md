```
psnr(a, b, maxv)
```

Compute the peak signal-to-noise ratio between two arrays `a` and `b`. `maxv` is the maximum possible value either array can take. The PSNR is computed as `10 * log10(maxv^2 / msd(a, b))`.
