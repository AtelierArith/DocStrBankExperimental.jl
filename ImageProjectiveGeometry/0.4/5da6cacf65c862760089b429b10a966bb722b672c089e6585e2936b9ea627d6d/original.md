hessianfeatures  - Computes determiant of hessian features in an image.

```
Usage: hdet = hessianfeatures(img, sigma)

Arguments:
            img      - Greyscale image to be processed.
                       ::Array{T,2} or ::ImageMeta{T,2} 
            sigma    - Defines smoothing scale.

Returns:    hdet     - Matrix of determinants of Hessian
```

The local maxima of hdet tend to mark the centres of dark or light blobs. However, the point that gets localised can be dependent on scale.  If the blobs you wish to detect are large you will need to use a value of sigma that is comparable in magnitude.

The local minima of hdet is useful for marking the intersection points of a camera calibration checkerboard pattern.  These saddle features seem to be more stable under scale variations.

For example to get the 100 strongest saddle features in image `img` use:

```
 > hdet = hessianfeatures(img, 1)      # sigma = 1
 > (r, c) = nonmaxsuppts(-hdet, N=100)
```

If the input is an ImageMeta cimg will be an ImageMeta with property spatialorder set to ["y","x"].

See also: harris(), noble(), shi_tomasi(), derivative5(), nonmaxsuppts()
