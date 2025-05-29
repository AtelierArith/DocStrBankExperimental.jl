```
biplot(table; kind=:form, dim=2, [aesthetics...])
```

Biplot of `table` of given `kind` in `dim`-dimensional space.

There are four kinds of biplots:

  * `:form`  - standard biplot with shape parameter `α = 1`
  * `:cov`   - standard biplot with shape parameter `α = 0`
  * `:rform` - relative variation biplot with `α = 1`
  * `:rcov`  - relative variation biplot with `α = 0`

# Biplot attributes

  * `kind` - kind of biplot (`:form`, `:cov`, `:rform` or `:rcov`)
  * `dim`  - number of dimensions `dim ∈ {2,3}` (default to `2`)

# Aesthetics attributes

  * `axescolormap` - colormap of principal axes (default to theme colormap)
  * `dotcolormap`  - colormap of sample dots (default to theme colormap)
  * `fontsize`     - font size in axes and dots (default to `12`)
  * `axesbody`     - size of principal axes' body (depends on `dim`)
  * `axeshead`     - size of principal axes' head (depends on `dim`)
  * `axescolor`    - color of principal axes (default to `:black`)
  * `axeslabel`    - names of principal axes (default to `x1,x2,...`)
  * `dotsize`      - size of sample dots (depends on `dim`)
  * `dotcolor`     - color of sample dots (default to `:black`)
  * `dotlabel`     - names of sample dots (default to `1:nobs`)
  * `showdots`     - show names of dots (default to `true`)
  * `showlinks`    - show links between principal axes (default to`false`)

See https://en.wikipedia.org/wiki/Biplot.

## References

  * Gabriel, K. 1971. [The Biplot Graphic Display of Matrices with Application to Principal Component Analysis](https://www.jstor.org/stable/2334381)
  * Aitchison, J. & Greenacre, M. 2002. [Biplots of Compositional data](https://rss.onlinelibrary.wiley.com/doi/abs/10.1111/1467-9876.00275)
