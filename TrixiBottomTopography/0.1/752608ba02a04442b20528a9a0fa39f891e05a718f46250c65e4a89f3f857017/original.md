```
BilinearBSpline(x::Vector, y::Vector, z::Matrix)
```

This function calculates the inputs for the structure [`BilinearBSpline`](@ref). The input values are:

  * `x`: Vector that contains equally spaced values in x-direction
  * `y`: Vector that contains equally spaced values in y-direction where the spacing between the      y-values has to be the same as the spacing between the x-values
  * `z`: Matrix that contains the corresponding values in z-direction.      Where the values are ordered in the following way:

$$
\begin{aligned}
   \begin{matrix}
        & & x_1 & x_2 & ... & x_n\\
        & & & & &\\
        y_1 & & z_{11} & z_{12} & ... & z_{1n}\\
        y_1 & & z_{21} & z_{22} & ... & z_{2n}\\
        \vdots & & \vdots & \vdots & \ddots & \vdots\\
        y_m & & z_{m1} & z_{m2} & ... & z_{mn}
   \end{matrix}
\end{aligned}
$$

Bilinear B-spline interpolation is only possible if we have at least two values in `x` and two values in `y` and the dimensions of vectors `x` and `y` correspond with the dimensions of the matrix `z`.

First of all the data is sorted which is done by [`sort_data`](@ref) to guarantee that the `x` and `y` values are in ascending order with corresponding matrix `z`.

The patch size `Delta` is calculated by subtracting the second by the first `x` value. This can be done because we only consider equal space between consecutive `x` and `y` values. A patch is the area between two consecutive `x` and `y` values.

For bilinear B-spline interpolation, the control points `Q` correspond with the `z` values.

The coefficients matrix `IP` for bilinear B-splines is fixed to be

$$
\begin{aligned}
  \begin{pmatrix}
    -1 & 1\\
    1 & 0
  \end{pmatrix}
\end{aligned}
$$

A reference for the calculations in this script can be found in Chapter 2 of

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
