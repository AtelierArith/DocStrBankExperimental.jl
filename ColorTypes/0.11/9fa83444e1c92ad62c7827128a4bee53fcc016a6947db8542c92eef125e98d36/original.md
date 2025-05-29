`TransparentColor{C,T,N}` is the abstract type for any color-with-transparency.  The `C` parameter refers to the type of the pure color (without transparency) and can be extracted with `color_type`. `T` is the element type of both `C` and the `alpha` channel, and `N` has the same meaning as in `Colorant` (and is 1 larger than the corresponding color type).

All transparent types should support two modes of construction:

```
P(color, alpha)
P(component1, component2, component3, alpha) (assuming a 3-component color)
```

For a `Colorant` `c`, the color component can be extracted with `color(c)`, and the alpha channel with `alpha(c)`. Note that types such as `ARGB32` do not have a field named `alpha`.

Most concrete types, like `RGB`, have both `ARGB` and `RGBA` transparent analogs.  These two indicate different internal storage order (see `AlphaColor` and `ColorAlpha`, and the `alphacolor` and `coloralpha` functions).
