Uses nonlinear least squares to fit the modified King's law:

`E^2 = A + B*U^n`

The Original (linear) King's law is used to estimate `A` and `B` when `n=1/2`.  This initial value is used as an initial guess for fitting the nonlinear modified King's law using the function `nonlinear_fit`.
