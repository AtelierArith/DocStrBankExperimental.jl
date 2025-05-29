```
binarize(image, predicate)
```

Binarize an image and return a region.

The predicate must be a funtion that takes a pixel value and returns a boolean result based on the pixel value.

Here are some useful examples:

# the returned region will contain all pixels > 0.3

reg = binarize(img, x -> x > 0.3)

# the returned region will contain all pixels <= 0.5

reg = binarize(img, x -> x <= 0.5)

# the returned region will contain all pixels between 0.3 and 0.8

reg = binarize(img, x -> x > 0.3 && x < 0.8)
