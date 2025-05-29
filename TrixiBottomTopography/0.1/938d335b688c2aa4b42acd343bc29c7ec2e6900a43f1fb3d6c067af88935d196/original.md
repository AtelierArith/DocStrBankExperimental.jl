```
BicubicBSpline(x::Vector, y::Vector, z::Matrix; end_condition = "free", smoothing_factor = 0.0)
```

This function calculates the inputs for the structure [`BicubicBSpline`](@ref). The input values are:

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

  * `end_condition`: a string which can either be "free" or "not-a-knot" and defines which                  end condition should be considered. By default this is set to "free".
  * `smoothing_factor`: a Float64 $\geq$ 0.0 which specifies the degree of smoothing of the `z`                     values. By default this value is set to 0.0 which corresponds to no                     smoothing.

Bicubic B-spline interpolation is only possible if the dimensions of vectors `x` and `y` correspond with the dimensions of the matrix `z`.

First, the data is sorted via [`sort_data`](@ref) to guarantee that the `x` and `y` values are in ascending order with corresponding matrix `z`.

The patch size `Delta` is calculated by subtracting the second by the first `x` value. This can be done because we only consider equal space between consecutive `x` and `y` values. A patch is the area between two consecutive `x` and `y` values.

If a `smoothing_factor` $>$ 0.0 is set, the function [`calc_tps`](@ref) calculates new values for `z` which guarantee a resulting parametric B-spline surface with less curvature.

The coefficients matrix `IP` for bicubic B-splines is fixed to be

$$
\begin{aligned}
    \begin{pmatrix}
        -1 & 3 & -3 & 1\\
        3 & -6 & 3 & 0\\
        -3 & 0 & 3 & 0\\
        1 & 4 & 1 & 0
    \end{pmatrix}
\end{aligned}
$$

To get the matrix of control points `Q` which is necessary to set up an interpolation function, we need to define a matrix `Phi` which maps the control points to a vector `P`. This can be done by solving the following system of linear equations for `Q`.

$$
\underbrace{
    \begin{bmatrix}
        z_{1,1} \\ z_{1,2} \\ \vdots \\ z_{1,n} \\ z_{2,1} \\ \vdots \\ z_{m,n} \\ 0 \\ \vdots \\ 0
    \end{bmatrix}
    }_{\text{:=P} \in \mathbb{R}^{(m+2)(n+2)\times 1}} = \frac{1}{36}
    \Phi \cdot
    \underbrace{\begin{bmatrix}
        Q_{1,1} \\ Q_{1,2} \\ \vdots \\ Q_{1,n+2} \\ Q_{2,1} \\ \vdots \\ Q_{m+2,n+2}
    \end{bmatrix}}_{\text{:= Q} \in \mathbb{R}^{(m+2) \times (n+2)}}
$$

For the first `n` $\cdot$ `m` lines, the matrix `Phi` is the same for the "free" end and the "not-a-knot" end condition. These lines have to address the following condition:

$$
\begin{align*}
    z_{j,i} = \frac{1}{36} \Big( &Q_{j,i} + 4Q_{j+1,i} + Q_{j+2,i} + 4Q_{j,i+1} + 16Q_{j+1,i+1}\\
    &+ 4Q_{j+2,i+1} + Q_{j,i+2} + 4Q_{j+1,i+2} + Q_{j+2,i+2} \Big)
\end{align*}
$$

for i = 1,...,n and j = 1,...,m.

The "free" end condition needs at least two values for the `x` and `y` vectors. The "free" end condition has the following additional requirements for the control points which have to be addressed by `Phi`:

  * $Q_{j,1} - 2Q_{j,2} + Q_{j,3} = 0$ for j = 2,...,m+1
  * $Q_{j,n} - 2Q_{j,n+1} + Q_{j,n+2} = 0$ for j = 2,...,m+1
  * $Q_{1,i} - 2Q_{2,i} + Q_{3,i} = 0$ for i = 2,...,n+1
  * $Q_{m,i} - 2Q_{m+1,i} + Q_{m+2,i} = 0$ for i = 2,...,n+1
  * $Q_{1,1} - 2Q_{2,2} + Q_{3,3} = 0$
  * $Q_{m+2,1} - 2Q_{m+1,2} + Q_{m,3} = 0$
  * $Q_{1,n+2} - 2Q_{2,n+1} + Q_{3,n} = 0$
  * $Q_{m,n} - 2Q_{m+1,n+1} + Q_{m+2,n+2} = 0$

The "not-a-knot" end condition needs at least four values for the `x` and `y` vectors.

  * Continuity of the third `x` derivative between the leftmost and second leftmost patch
  * Continuity of the third `x` derivative between the rightmost and second rightmost patch
  * Continuity of the third `y` derivative between the patch at the top and the patch below
  * Continuity of the third `y` derivative between the patch at the bottom and the patch above
  * $Q_{1,1} - Q_{1,2} - Q_{2,1} + Q_{2,2} = 0$
  * $Q_{m-1,1} + Q_{m,1} + Q_{m-1,2} - Q_{m,2} = 0$
  * $Q_{1,n-1} + Q_{2,n} + Q_{1,n-1} - Q_{2,n} = 0$
  * $Q_{m-1,n-1} - Q_{m,n-1} - Q_{m-1,n} + Q_{m,n} = 0$

A reference for the calculations in this script can be found in Chapter 2 of

  * Quentin Agrapart & Alain Batailly (2020), Cubic and bicubic spline interpolation in Python. [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
