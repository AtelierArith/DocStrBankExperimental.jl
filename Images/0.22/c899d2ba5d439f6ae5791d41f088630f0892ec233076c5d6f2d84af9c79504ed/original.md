```
thinned = thin_edges(img, gradientangle, [border])
thinned, subpix = thin_edges_subpix(img, gradientangle, [border])
thinned, subpix = thin_edges_nonmaxsup(img, gradientangle, [border]; [radius::Float64=1.35], [theta=pi/180])
thinned, subpix = thin_edges_nonmaxsup_subpix(img, gradientangle, [border]; [radius::Float64=1.35], [theta=pi/180])
```

Edge thinning for 2D edge images.  Currently the only algorithm available is non-maximal suppression, which takes an edge image and its gradient angle, and checks each edge point for local maximality in the direction of the gradient. The returned image is non-zero only at maximal edge locations.

`border` is any of the boundary conditions specified in `padarray`.

In addition to the maximal edge image, the `_subpix` versions of these functions also return an estimate of the subpixel location of each local maxima, as a 2D array or image of `Graphics.Point` objects.  Additionally, each local maxima is adjusted to the estimated value at the subpixel location.

Currently, the `_nonmaxsup` functions are identical to the first two function calls, except that they also accept additional keyword arguments.  `radius` indicates the step size to use when searching in the direction of the gradient; values between 1.2 and 1.5 are suggested (default 1.35).  `theta` indicates the step size to use when discretizing angles in the `gradientangle` image, in radians (default: 1 degree in radians = pi/180).

Example:

```
g = rgb2gray(rgb_image)
gx, gy = imgradients(g)
mag, grad_angle = magnitude_phase(gx,gy)
mag[mag .< 0.5] = 0.0  # Threshold magnitude image
thinned, subpix =  thin_edges_subpix(mag, grad_angle)
```
