Construct an Akima spline according to [1]. In addition to the original method, this implementation also allows for customized extrapolation at both spline sides. The extrapolation behaviour is defined by the coefficients of a 3rd degree polynomial which can be given as additional keyword arguments extrapl and extrapr to the constructor. extrapl and/or extrapr should be either "nothing" or a set of coefficients.

# Case 1: Extrapolation is set to "nothing"

In this case, the default quadratic extrapolation according to section 2.3 of [1] is used to construct the spline and the spline throws an error when evaluated outside its boundaries.

# Case 2: Extrapolation is set to a vector

The container is given as a n-element collection of values:     extrapl = [p1, p2, p3, ..., pn] which are used to evaluate the following function:     y = p0 + p1*(x-x3) + p2*(x-x3)^2 + p3*(x-x3)^3 + ... + pn*(x-x3)^n The constant p0 is equal to y3 by definition (continuous spline). x3 and y3 are the first/last datapoint values respectively.
