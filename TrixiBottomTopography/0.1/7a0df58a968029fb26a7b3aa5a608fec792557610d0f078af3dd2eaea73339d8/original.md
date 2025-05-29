```
LinearBSpline(x::Vector, y::Vector)
```

This function calculates the inputs for the structure [`LinearBSpline`](@ref). The input values are:

  * `x`: A vector that contains equally spaced values in x-direction
  * `y`: A vector that contains values in y-direction

Linear B-spline interpolation is only possible if the data set has at least two values in `x`.

First the data is sorted via [`sort_data`](@ref) to guarantee that the `x` values are in ascending order.

The patch size `Delta` is calculated by subtracting the second and first `x` values. This can be done because we only consider equally spaced `x` values. A patch is the area between two consecutive `x` values.

For linear B-spline interpolation, the control points `Q` correspond with the values in `y`.

The coefficients matrix `IP` for linear B-splines is fixed to be

$$
\begin{aligned}
  \begin{pmatrix}
    -1 & 1\\
    1 & 0
  \end{pmatrix}
\end{aligned}
$$

A reference for the calculations in this script can be found in Chapter 1 of

  * Quentin Agrapart & Alain Batailly (2020),  Cubic and bicubic spline interpolation in Python.  [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
