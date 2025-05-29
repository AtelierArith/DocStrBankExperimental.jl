```
sineramp(rows, cols;
        amplitude = 12.5,
        wavelength = 8,
        p = 2)
```

Generate a `rows × cols` array of values which show a sine wave with decreasing amplitude from top to bottom.

Usage:

```julia
using Images
scheme = ColorSchemes.dracula
img = Gray.(sineramp(256, 512, amp = 12.5, wavelen = 8, p = 2))
cimg = zeros(RGB, 256, 512)
for e in eachindex(img)
    cimg[e] = get(mscheme, img[e])
end
cimg
```

The default wavelength is 8 pixels. On a computer monitor with a nominal pixel pitch of 0.25mm this corresponds to a wavelength of 2mm. With a monitor viewing distance of 600mm this corresponds to 0.19 degrees of viewing angle or approximately 5.2 cycles per degree. This falls within the range of spatial frequencies (3-7 cycles per degree) at which most people have maximal contrast sensitivity to a sine wave grating (this varies with mean luminance). A wavelength of 8 pixels is also sufficient to provide a reasonable discrete representation of a sine wave. The aim is to present a stimulus that is well matched to the performance of the human visual system so that what we are primarily evaluating is the colorscheme's perceptual contrast and not the visual performance of the viewer.

The default amplitude is set at 12.5, so that from peak to trough we have a local feature of magnitude 25. This is approximately 10% of the 256 levels in a typical colorscheme. It is not uncommon for colorschemes to have perceptual flat spots that can hide features of this magnitude.

The width of the image is adjusted so that we have an integer number of cycles of the sinewave. This helps should one be using the test image to evaluate a cyclic colorscheme. However you will still see a slight cyclic discontinuity at the top of the image, though this will disappear at the bottom.
