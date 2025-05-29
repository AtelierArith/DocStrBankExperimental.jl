```
Colorfier(values; [alphas, colorscheme, colorrange])
```

Maps each value in `values` to a color. Colors can be obtained using the [`Colorfy.colors`](@ref) function.

## Options

  * `alphas` - Scalar or a vector of color alphas (default to `Colorfy.defaultalphas(values)`);
  * `colorscheme` - Scheme name or a `ColorSchemes.ColorScheme` object (default to `Colorfy.defaultcolorscheme(values)`);
  * `colorrange` - Tuple with minimum and maximum color values or a symbol that can be passed  to the `rangescale` argument of the `ColorSchemes.get` function (default to `Colorfy.defaultcolorrange(values)`);
