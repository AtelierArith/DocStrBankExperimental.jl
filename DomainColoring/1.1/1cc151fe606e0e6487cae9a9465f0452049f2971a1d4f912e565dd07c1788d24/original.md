```
checkerplot(
    f :: "Complex -> Complex",
    limits = (-1, 1, -1, 1);
    pixels = (720, 720),
    real = false,
    imag = false,
    rect = false,
    angle = false,
    abs = false,
    polar = false,
    box = nothing,
    hicontrast = false,
    kwargs...
)
```

Takes a complex function and produces a checker plot.

# Arguments

  * **`f`** is the complex function to plot.
  * **`limits`** are the limits of the rectangle to plot, in the format `(minRe, maxRe, minIm, maxIm)`, if one or two numbers are provided instead they are take symmetric along the real and imaginary axis.

# Keyword Arguments

  * **`pixels`** is the number of pixels to compute in, respectively, the real and imaginary axis, taking the same for both if only one number is provided.

If none of the below options are set, the plot defaults to `rect = true`.

  * **`real`** plots black and white stripes orthogonal to the real axis at a rate of one stripe per unit increase. If set to a number this will be used as width instead.
  * **`imag`** plots black and white stripes orthogonal to the imaginary axis at a rate of one stripe per unit increase. If set to a number this will be used as width instead.
  * **`rect`** is a shortcut for `real = true` and `imag = true`.
  * **`angle`** plots black and white stripes orthogonal to the phase angle at a rate of eight stripes per full rotation. Can be set to an integer to specify a different rate.
  * **`abs`** plots black and white stripes at a rate of one stripe per unit increase of the natural logarithm of the magnitude. If set to a number this is used as the base of the logarithm. When set to a function, unit increases of its output are used instead.
  * **`polar`** is a shortcut for `angle = true` and `abs = true`. Can also be set to the basis to use for `abs`, then a suitable rate for `angle` will be selected.
  * **`box`** if set to `(a, b, s)` shades the area where the output is within the box `a` and `b` in the color `s` when set to `(f, s)` the colored domain is defined by `f(w) == true`. Can also be a list of multiple boxes.
  * **`hicontrast`** uses black and white instead of the softer defaults.

Remaining keyword arguments are passed to the plotting backend.
