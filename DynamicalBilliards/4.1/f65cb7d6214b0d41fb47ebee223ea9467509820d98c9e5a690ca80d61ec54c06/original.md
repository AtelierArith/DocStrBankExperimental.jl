```
ellipse_arclength(θ, e::Ellipse)
```

Return the arclength of the ellipse that spans angle `θ` (in normal coordinates, not in the ellipse parameterization). Expects `θ` to be in `[0, 2π]`.

After properly calculating the

$$
d=b\,E\bigl(\tan^{-1}(a/b\,\tan(\theta))\,\big|\,1-(a/b)^2\bigr)
$$
