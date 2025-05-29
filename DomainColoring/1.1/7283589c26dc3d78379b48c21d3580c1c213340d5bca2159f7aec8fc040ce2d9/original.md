```
domaincolor(
    f :: "Complex -> Complex",
    limits = (-1, 1, -1, 1);
    pixels = (720, 720),
    abs = false,
    grid = false,
    color = true,
    all = false,
    box = nothing,
    kwargs...
)
```

Takes a complex function and produces its domain coloring plot.

Red corresponds to phase $0$, yellow to $\frac{\pi}{3}$, green to $\frac{2\pi}{3}$, cyan to $\pi$, blue to $\frac{4\pi}{3}$, and magenta to $\frac{5\pi}{3}$.

# Arguments

  * **`f`** is the complex function to plot.
  * **`limits`** are the limits of the rectangle to plot, in the format `(minRe, maxRe, minIm, maxIm)`, if one or two numbers are provided instead they are take symmetric along the real and imaginary axis.

# Keyword Arguments

  * **`pixels`** is the number of pixels to compute in, respectively, the real and imaginary axis, taking the same for both if only one number is provided.
  * **`abs`** toggles the plotting of the natural logarithm of the magnitude as lightness ramps between level curves. If set to a number, this will be used as base of the logarithm instead, if set to `Inf`, zero magnitude will be colored black and poles white. Further granular control can be achieved by passing a named tuple with any of the parameters `base`, `transform`, or `sigma`. `base` changes the base of the logarithm, as before. `transform` is the function applied to the magnitude (`m -> log(base, m)` by default), and `sigma` changes the rate at which zeros and poles are colored and implies `base = Inf`.
  * **`grid`** plots points with integer real or imaginary part as black dots. More complicated arguments can be passed as a named tuple in a similar fashion to [`checkerplot`](@ref).
  * **`color`** toggles coloring of the phase angle. Can also be set to either the name of, or a `ColorScheme`, or a function `θ -> Color`. If set to `:print` a desaturated version of the default is used.
  * **`all`** is a shortcut for `abs = true`, `grid = true`, and `color = true`.
  * **`box`** if set to `(a, b, s)` shades the area where the output is within the box `a` and `b` in the color `s` when set to `(f, s)` the colored domain is defined by `f(w) == true`. Can also be a list of multiple boxes.

Remaining keyword arguments are passed to the plotting backend.
