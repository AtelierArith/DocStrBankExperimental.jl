```
spline_interpolation(b_spline::LinearBSpline, x::Number)
```

The inputs are the [`LinearBSpline`](@ref) object and a variable `x` at which the spline will be evaluated.

The parameter `i` indicates the patch in which the variable `x` is located. This parameter is also used to get the correct control points from `Q`. A patch is the area between two consecutive `b_spline.x` values.

`kappa` is an interim variable which maps `x` to the interval $[0,1]$ for further calculations.

To evaluate the spline at `x`, we have to calculate the following:

$$
\begin{aligned}
c_{i,1}(\kappa_i(x)) =
    \begin{bmatrix}
        \kappa_i(x)\\ 1
    \end{bmatrix}^T
    \begin{bmatrix}
        -1 & 1\\1 & 0
    \end{bmatrix}
    \begin{bmatrix}
        Q_i\\Q_{i+1}
    \end{bmatrix}
\end{aligned}
$$

A reference for the calculations in this script can be found in Chapter 1 of

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
