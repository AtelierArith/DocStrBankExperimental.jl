```
RungeKuttaConvolutionQuadrature{T,N,NN}
```

T: the value type of the basis function. N: the number of stages. NN: N*N.

Performs a convolution quadrature on a laplaceKernel to represent an operator in time domain using an implicit Runge-Kutta method.

laplaceKernel: function of the Laplace variable s that returns an IntegralOperator. A, b: Coefficient matrix and vectors from the Butcher tableau. Δt: time step. zTransformedTermCount: Number of terms in the inverse Z-transform. contourRadius: radius of circle used as integration contour for the inverse Z-transform.
