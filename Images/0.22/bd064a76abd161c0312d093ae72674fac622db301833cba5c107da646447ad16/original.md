```
canny_edges = canny(img, (upper, lower), sigma=1.4)
```

Performs Canny Edge Detection on the input image.

Parameters :

(upper, lower) :  Bounds for hysteresis thresholding   sigma :           Specifies the standard deviation of the gaussian filter

# Example

```julia
imgedg = canny(img, (Percentile(80), Percentile(20)))
```
