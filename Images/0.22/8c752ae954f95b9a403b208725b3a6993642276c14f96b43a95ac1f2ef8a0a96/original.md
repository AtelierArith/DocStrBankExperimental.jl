```
pyramid = gaussian_pyramid(img, n_scales, downsample, sigma)
```

Returns a  gaussian pyramid of scales `n_scales`, each downsampled by a factor `downsample` > 1 and `sigma` for the gaussian kernel.
