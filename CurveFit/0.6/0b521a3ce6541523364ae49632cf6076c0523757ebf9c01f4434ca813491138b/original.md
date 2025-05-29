# Generic interface for curve fitting.

The same function `curve_fit` can be used to fit the data depending on fit type,  which is specified in the first parameter. This function returns an object that can be used to estimate the value of the fitting model using function `apply_fit`.

## A few examples:

  * `f = curve_fit(LinearFit, x, y)`
  * `f = curve_fit(Polynomial, x, y, n)`

Other types of fit include: LogFit, PowerFit, ExpFit, LinearKingFit, KingFit, RationalPoly. See the documentation for details.
