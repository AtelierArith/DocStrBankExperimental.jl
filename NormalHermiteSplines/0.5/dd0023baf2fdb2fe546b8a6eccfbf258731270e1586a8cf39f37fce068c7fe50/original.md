`estimate_cond(spline::NormalSpline{T, RK}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Get an estimation of the Gram matrix condition number. It needs the `spline` object is prepared and requires O(N^2) operations. (C. Brás, W. Hager, J. Júdice, An investigation of feasible descent algorithms for estimating the condition number of a matrix. TOP Vol.20, No.3, 2012.)

# Arguments

  * `spline`: the `NormalSpline` object returned by `prepare`, `construct` or `interpolate` function.

Return: an estimation of the Gram matrix condition number.
