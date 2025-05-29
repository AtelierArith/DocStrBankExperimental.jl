```
t8_geom_linear_interpolation(coefficients, corner_values, corner_value_dim, interpolation_dim, evaluated_function)
```

Interpolates linearly between 2, bilinearly between 4 or trilineraly between 8 points.

# Arguments

  * `coefficients`:[in] An array of size at least dim giving the coefficients used for the interpolation
  * `corner_values`:[in] An array of size 2^dim * 3, giving for each corner (in zorder) of the unit square/cube its function values in space.
  * `corner_value_dim`:[in] The dimension of the *corner_values*.
  * `interpolation_dim`:[in] The dimension of the interpolation (1 for linear, 2 for bilinear, 3 for trilinear)
  * `evaluated_function`:[out] An array of size *corner*value*dim*, on output the result of the interpolation.

### Prototype

```c
void t8_geom_linear_interpolation (const double *coefficients, const double *corner_values, int corner_value_dim, int interpolation_dim, double *evaluated_function);
```
