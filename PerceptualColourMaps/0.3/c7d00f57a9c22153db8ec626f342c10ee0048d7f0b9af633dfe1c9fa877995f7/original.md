ternaryimage:  Perceptualy uniform ternary image from 3 bands of data

This function generates a ternary image using 3 basis colours that are closely matched in lightness, as are their secondary colours.  The colours are not as vivid as the RGB primaries but they produce ternary images with consistent feature salience no matter what permutation of channel-colour assignement is used.  This is in contrast to ternary images constructed with the RGB primaries where the channel that happens to get encoded in green dominates the perceptual result.

Useful for Landsat imagery or radiometric images.

```
Usage: rgbimg = ternaryimage(img; bands, histcut, RGB)

Argument:
            img - Multiband image with at least 3 bands.
                  ::ImageMeta{T,3} or ::Array{T<:Real,3}

Keyword Arguments:
          bands - Array of 3 values indicating the bands, to be assigned to
                  the red, green and blue basis colour maps.  If omitted
                  bands defaults to [1, 2, 3].
        histcut - Percentage of image band histograms to clip.  It can be
                  useful to clip 1-2%. If you see lots of white in your
                  ternary image you have clipped too much. Defaults to 0.
            RGB - Boolean flag, if set to true the classical RGB primaries
                  are used to construct the ternary image rather than the
                  lightness matched primaries. Defaults to false.

Returns:
          rgbimg - RGB ternary image
                  ::ImageMeta{T,3} or ::Array{T<:Real,3}
```

For the derivation of the three primary colours see: Peter Kovesi. Good Colour Maps: How to Design Them. arXiv:1509.03700 [cs.GR] 2015.

See also: applycolourmap, linearrgbmap
