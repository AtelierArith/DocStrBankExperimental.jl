```
spline_interpolation(b_spline::BilinearBSpline, x::Number, y::Number)
```

The inputs are the [`BilinearBSpline`](@ref) object and the variable `x` and `y` at which the spline will be evaluated.

The parameters `i` and `j` indicate the patch in which `(x,y)` is located. This information is also used to get the correct control points from `Q`. A patch is the area between two consecutive `b_spline.x` and `b_spline.y` values.

`my` is  an interim variable that maps `x` to the interval $[0,1]$ for further calculations. `ny` does the same for `y`.

To evaluate the spline at `(x,y)`, we have to calculate the following:

$$
\begin{aligned}
c_{i,j,1}(\mu_i(x),\nu_j(y)) =
    \begin{bmatrix} \nu_j(y)\\ 1 \end{bmatrix}^T
    \underbrace{\begin{bmatrix} -1 & 1\\ 1 & 0 \end{bmatrix}}_{\text{IP}}
    \begin{bmatrix} Q_{i,j} & Q_{i,j+1}\\ Q_{i+1,j} & Q_{i+1,j+1} \end{bmatrix}
    \underbrace{\begin{bmatrix} -1 & 1\\ 1 & 0 \end{bmatrix}}_{\text{IP}^T}
    \begin{bmatrix} \mu_i(x) \\ 1\end{bmatrix}
\end{aligned}
$$

A reference for the calculations in this script can be found in Chapter 2 of

  * Quentin Agrapart & Alain Batailly (2020) Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
