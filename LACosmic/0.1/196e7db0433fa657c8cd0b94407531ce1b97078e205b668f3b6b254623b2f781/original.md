```
lacosmic(data::AbstractMatrix;
    noise=nothing,
    gain=1,
    background=0,
    readnoise=0,
    mask=falses(size(data)),
    sigma_clip=4.5,
    contrast=5,
    neighbor_thresh=0.3,
    maxiter=4,
    saturation_level=2^16,
    block_size=2)
```

Laplacian cosmic ray detection (LACosmic). This algorithm implements the algorithm presented in [lacosmicx](https://github.com/cmccully/lacosmicx). The return values are the cleaned image and the bad pixel mask. The image cleaning is done via median interpolation.

# Parameters

  * `noise` is the pre-determined estimate of the data noise (square root of variance), if any
  * `gain` is the image gain in electrons per data number
  * `background` is pre-determined image background, if any
  * `readnoise` is the read noise of the image in electrons
  * `mask` is an input bad pixel mask, where `true` represents a bad pixel
  * `sigma_clip` is the Laplacian signal-to-noise ratio for flagging bad pixels
  * `contrast` is the minimum contrast required to flag a bad pixel in the ratio of the Laplacian image to the fine-structure image
  * `neighbor_thresh` is the fractional detection limit for cosmic rays surrounding other cosmic rays. Should be a number between 0 and 1.
  * `maxiter` is the maximum number of iterations used for detecting bad pixels
  * `saturation_level` is the saturation value in electrons
  * `block_size` is the subsampling factor for the Laplacian filter image.

# Examples

```jldoctest
julia> image = 100 .* randn(1001, 1001) .+ 1000;

julia> clean_image, mask = lacosmic(image, gain=4);
```

# References

> [van Dokkum, P.G. (2001)](https://ui.adsabs.harvard.edu/abs/2001PASP..113.1420V/abstract) - "Cosmic-Ray Rejection by Laplacian Edge Detection"

