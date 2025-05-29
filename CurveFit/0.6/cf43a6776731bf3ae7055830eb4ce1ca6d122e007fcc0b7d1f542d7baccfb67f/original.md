# Simple Least Squares fitting

The `CurveFit` module provides functions that implement a few least squares approximations.

It is simple in an engineering sense. It simply returns the coefficients and does not do  any error analysis. 

It does, however, provide a simple and common interface to the routines.

The package also includes nonlinear least squares fitting using a Newton type algorithm

The fitting algorithms include

  * Straight lines
  * Polynomial fitting
  * Power laws
  * Log laws
  * Exp laws
  * Rational polynomial fitting
  * A generic non-linear fitting algorithm
  * King's law (used in hotwire anemometry)
