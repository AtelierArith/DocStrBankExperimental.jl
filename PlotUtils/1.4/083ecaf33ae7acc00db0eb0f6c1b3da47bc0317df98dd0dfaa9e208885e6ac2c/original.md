```
zscale(input::AbstractArray,
    nsamples=1000;
    contrast=0.25,
    max_reject=0.5,
    min_npixels=5,
    k_rej=2.5,
    max_iterations=5)
```

Implementation of the `zscale` IRAF function for finding colorbar limits of `input`, which showcase data near the median. This is useful for data with extreme outliers, such as astronomical images.

## Keyword arguments

  * `nsamples` - The number of samples to use from `input`. If fewer than `nsamples` are present, will use the full input
  * `contrast` - The desired contrast
  * `k_rej` - The number of standard deviations above which data is rejected
  * `max_iteration` - The number of iterations used for fitting samples
  * `max_reject` - The maximum number of pixels to reject during the iterative fitting
  * `min_npixels` - The minimum number of pixels to calculate the limits after the iterative fitting

See the extended help (in REPL, `??zscale`) for technical details.

## Examples

```jldoctest
julia> img = 0:9999

julia> zscale(img)
(0, 9990)
```

## Extended help

## Description

The zscale algorithm is designed to display the image values near the median image value, without the time consuming process of computing a full image histogram.

This is particularly useful for astronomical images, which generally have a very peaked histogram corresponding to the background sky in direct imaging, or the continuum in a two dimensional spectrum.

A subset of the image is examined, and approximately `nsamples` pixels are sampled evenly over the image. The number of lines is a user parameter, `nsample_lines`.

The pixels are ranked in brightness to form the function `I(i)`, where `i` is the rank of the pixel, and `I` is its value. Generally, the midpoint of this function (the median) is very near the peak of the image histogram.  There is a well defined slope about the midpoint, which is related to the width of the histogram.

At the ends of the `I(i)` function, there are a few very bright and dark pixels due to objects and defects in the field. To determine the slope, a linear function is fit with iterative rejection:

```
I(i) = intercept + slope * (i - midpoint)
```

If more than half of the points are rejected, then there is no well defined slope, and the full range of the sample defines `z1` and `z2`. Otherwise, the endpoints of the linear function are used (provided they are within the original range of the sample):

```
z1 = I(midpoint) + (slope / contrast) * (1 - midpoint)
z2 = I(midpoint) + (slope / contrast) * (npoints - midpoint)
```
