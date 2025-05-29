```
t8_geom_triangular_interpolation(coefficients, corner_values, corner_value_dim, interpolation_dim, evaluated_function)
```

Triangular interpolation between 3 points (triangle) or 4 points (tetrahedron) using cartesian coordinates. The input coefficients have to be given as coordinates in the reference triangle (interpolation_dim = 2) with points (0,0) (1,0) (1,1) or the reference tet (interpolation_dim = 3) with points (0,0,0) (1,0,0) (1,1,0) (1,1,1).

# Arguments

  * `coefficients`:[in] An array of size *interpolation_dim* giving the coefficients in the reference triangle/tet used for the interpolation
  * `corner_values`:[in] An array of size  3 * *corner*value*dim* for *interpolation_dim* == 2 or 4 * *corner*value*dim* for *interpolation_dim* == 3,  giving the function values of the triangle/tetrahedron for each corner (in zorder)
  * `corner_value_dim`:[in] The dimension of the *corner_values*.
  * `interpolation_dim`:[in] The dimension of the interpolation (2 for triangle, 3 for tetrahedron)
  * `evaluated_function`:[out] An array of size *corner*value*dim*, on output the result of the interpolation.

### Prototype

```c
void t8_geom_triangular_interpolation (const double *coefficients, const double *corner_values, int corner_value_dim, int interpolation_dim, double *evaluated_function);
```
