`imgs = imstretch(img, m, slope)` enhances or reduces (for slope > 1 or < 1, respectively) the contrast near saturation (0 and 1). This is essentially a symmetric gamma-correction. For a pixel of brightness `p`, the new intensity is `1/(1+(m/(p+eps))^slope)`.

This assumes the input `img` has intensities between 0 and 1.
