```
CubicBSpline(x::Vector, y::Vector; end_condition = "free", smoothing_factor = 0.0)
```

This function calculates the inputs for the structure [`CubicBSpline`](@ref). The input values are:

  * `x`: Vector that contains equally spaces values in x-direction
  * `y`: Vector that contains values in y-direction
  * `end_condition`: String that can either be `free` or `not-a-knot` and defines which                  end condition should be considered. By default this is set to "free".
  * `smoothing_factor`: Float64 $\geq$ 0.0 which specifies the degree of smoothing of the `y`                     values. By default this value is set to `0.0` that corresponds to no                     smoothing.

First the data is sorted via [`sort_data`](@ref) to guarantee that the `x` values are in ascending order.

The patch size `Delta` is calculated by subtracting the second and first `x` value. This can be done because we only consider equally spaced `x` values. (A patch is the area between two consecutive `x` values)

If a `smoothing_factor` > 0.0 is set, the function [`spline_smoothing`](@ref) calculates new `y` values which guarantee a B-Spline with less curvature.

The coefficients matrix `IP` for linear B-splines is fixed to be

$$
\begin{aligned}
  IP = \begin{pmatrix}
    -1 & 3 & -3 & 1\\
    3 & -6 & 3 & 0\\
    -3 & 0 & 3 & 0\\
    1 & 4 & 1 & 0
  \end{pmatrix}
\end{aligned}
$$

The "free" end condition requires the second and the second to last control points lie between the first and the third control point and that the second to last control points are between the third to last and the last control point. This procedure is only possible with at least two values in `x` data. The system of linear equations to determine the control points have the following form:

$$
\begin{aligned}
    \underbrace{\begin{bmatrix}
            0 \\ P_1 \\ P_2 \\ \vdots \\ P_{n-1} \\ P_n\\ 0
        \end{bmatrix}}_{:= P^*_{\text{free}}}
        = \frac{1}{6}
    \underbrace{
        \begin{bmatrix}
            1 & -2 & 1 & 0 & ... & ... & 0 \\
            1      & 4 & 1 & 0 & ... & ... & 0\\
            0      & 1 & 4 & 1 & 0   &     &     \vdots\\
            \vdots &  0      & \ddots & \ddots & \ddots & 0 & \vdots\\
            \vdots &       & 0 & 1 & 4 & 1 & 0\\
            0 & ... & ... & 0 & 1 & 4 & 1\\
            0 & ... & ... & 0 & 1 & -2 & 1
        \end{bmatrix}
    }_{:= \Phi^*_{\text{free}}}
    \underbrace{\begin{bmatrix}
        Q_1 \\ Q_2 \\ Q_3 \\ \vdots \\ Q_n \\ Q_{n+1} \\ Q_{n+2}
    \end{bmatrix}}_{:= Q_{\text{free}}},
\end{aligned}
$$

which is solved for $Q_{\text{free}}$.

The "not-a-knot" end condition requires the continuity of the third derivative in the second and second to last fit knot. This end condition is only possible with at least four values in `x` data. The system of linear equations to determine the control points has the following form:

$$
\begin{aligned}
    \underbrace{\begin{bmatrix}
        0 \\ P_1 \\ P_2 \\ \vdots \\ P_{n-1} \\ P_n\\ 0
    \end{bmatrix}}_{:= P^*_{\text{not-a-knot}}}
    = \frac{1}{6}
    \underbrace{
        \begin{bmatrix}
            -1 & 4 & -6 & 4 & -1 & 0 &... &  0 \\
            1      & 4 & 1 & 0 & ... & ... & ... & 0\\
            0      & 1 & 4 & 1 & 0   &     &     &\vdots\\
            \vdots &  0      & \ddots & \ddots & \ddots & 0 & &\vdots\\
            \vdots &  & 0      & \ddots & \ddots & \ddots & 0 &\vdots\\
            \vdots &    &   & 0 & 1 & 4 & 1 & 0\\
            0 & ... & ...  & ... & 0 & 1 & 4 & 1\\
            0 & ... & 0 & -1 & 4 & -6 & 4 & -1
        \end{bmatrix}
    }_{:= \Phi^*_{\text{not-a-knot}}}
    \underbrace{\begin{bmatrix}
        Q_1 \\ Q_2 \\ Q_3 \\ \vdots \\ \vdots \\ Q_n \\ Q_{n+1} \\ Q_{n+2}
    \end{bmatrix}}_{:= Q_{\text{not-a-knot}}}.
\end{aligned}
$$

which is solved for $Q_{\text{not-a-knot}}$.

For both cases $P_1,...,P_n = y_1,...,y_n$.

A reference for the calculations in this script can be found in Chapter 1 of

  * Quentin Agrapart & Alain Batailly (2020),  Cubic and bicubic spline interpolation in Python.  [hal-03017566v2](https://hal.archives-ouvertes.fr/hal-03017566v2)
