```
out = hmin_transform(img, h)
```

Suppresses all minima in grayscale image whose depth is less than h.

H-minima transform is defined as the reconstruction by erosion of (img + h) by img. See Morphological image analysis by Soille pg 170-172.
