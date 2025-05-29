```
pyramid = gaussian_pyramid(img, n_scales, downsample, sigma)
```

スケール `n_scales` のガウシアンピラミッドを返し、各スケールはダウンサンプルファクター `downsample` > 1 とガウシアンカーネルのための `sigma` でダウンサンプルされます。
