```
boxplot(x, y; kwargs...)
```

Draw a Tukey style boxplot. The boxplot has 3 components:

  * a `crossbar` spanning the interquartile (IQR) range with a midline marking the   median
  * an `errorbar` whose whiskers span `range * iqr`
  * points marking outliers, that is, data outside the whiskers

# Arguments

  * `x`: positions of the categories
  * `y`: variables within the boxes

# Keywords

  * `orientation=:vertical`: orientation of box (`:vertical` or `:horizontal`)
  * `width=0.8`: width of the box
  * `show_notch=false`: draw the notch
  * `notchwidth=0.5`: multiplier of `width` for narrowest width of notch
  * `show_median=true`: show median as midline
  * `range`: multiple of IQR controlling whisker length
  * `whiskerwidth`: multiplier of `width` for width of T's on whiskers, or   `:match` to match `width`
  * `show_outliers`: show outliers as points
