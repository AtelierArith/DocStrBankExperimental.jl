```
spline_interpolation(b_spline::CubicBSpline, x::Number)
```

The inputs are the [`CubicBSpline`](@ref) object and a variable `x` at which the spline will be evaluated.

The parameter `i` indicates the patch in which the variable `x` is located. This parameter is also used to get the correct control points from `Q`. A patch is the area between two consecutive `b_spline.x` values.

`kappa` is  an interim variable which maps `t` to the interval $[0,1]$ for further calculations.

To evaluate the spline at `x`, we have to calculate the following:

$$
\begin{aligned}
c_{i,3}\left(\kappa_i(x) \right) = \frac{1}{6}
    \begin{bmatrix}
        \kappa_i(x)^3\\ \kappa_i(x)^2\\ \kappa_i(x) \\1
    \end{bmatrix}^T
    \underbrace{\begin{bmatrix}
        -1 & 3 & -3 & 1\\
        3 & -6 & 3 & 0\\
        -3 & 0 & 3 & 0\\
        1 & 4 & 1 & 0
    \end{bmatrix}}_{\text{IP}}
    \begin{bmatrix}
        Q_{i,\text{free}}\\ Q_{i+1,\text{free}}\\ Q_{i+2,\text{free}}\\ Q_{i+3,\text{free}}
    \end{bmatrix}
\end{aligned}
$$

A reference for the calculations in this script can be found in Chapter 1 of

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
