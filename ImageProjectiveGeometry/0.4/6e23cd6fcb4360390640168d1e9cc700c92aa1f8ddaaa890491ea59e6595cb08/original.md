stereorectifytransforms

Compute homographies that transform an image pair into a stereorectified pair.

```
Usage:  (P1r, H1, P2r, H2, dmin, dmax, dmed) = stereorectifytransforms(P1, img1, P2, img2,
                                   xy1=zeros(0), xy2=zeros(0); scale=1.0, disparitytruncation=0)

Arguments:
          P1, P2 - Projection matrices of the images to be rectified.
      img1, img2 - The two images, may be multi-channel (assumed same size).
         xy1,xy2 - Optional: Two sets of corresponding homogeneous image
                   coordinates in the images [3 x N] in size.  If supplied
                   these are used to construct a rectification that seeks
                   to minimise the relative displacement between the
                   rectified image points.
Keyword argument:
                scale - The desired scaling of the image, defaults to 1.0
  disparitytruncation - The percentage to be clipped off the ends of the histogram
                        of image coordiante disparities for the determination of
                        the disparity range.

Returns:
        P1r, P2r - The projection matrices of the rectified images.
          H1, H2 - Homographies that should be applied to img1 and img2 to
                   obtain a stereorectifed pair
      dmin, dmax - The range of disparities between the images derived from
                   the rectified image coordinates (if supplied).
            dmed - Median of disparities.
```

Note the value of supplying xy1 and xy2 is that the local spatial arrangement of pixels at any matching point between images is likely to be more similar and hence image descriptors are likely to work better.  Also, the disparity ranges between the images will be kept as uniform as possible.

The range of disparities is derived from a histogram of the disparities between the supplied image coordinates with a specified truncation applied to the ends of the histograms to exclude outliers.

See also: stereorectify()
