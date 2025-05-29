```
SingleSpline()
```

Quality function that interpolates all scaled data points to a single spline. The quality is then calculated as the sum of the squared differences between the data points and the interpolated values. The spline is fitted using the KissSmoothing.jl package. The number of knots can be specified using the `N_knots` keyword argument. If `N_knots` is not specified, the number of knots is set to `total_number_of_data_points / 10`.
