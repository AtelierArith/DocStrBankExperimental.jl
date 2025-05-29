Use Brent's method to find the root of a function, which is known to exist between xa and xb. The root is updated until its accuracy is tol. func is the name of the function to solve. The variable root is returned as the root of the function. The function being evaluated has the definition statement: 

`function [fx] = func (physcon, forcvar, surfvar, x)`

The function func is evaluated at x and the returned value is fx. It uses variables in the physcon, forcvar, surfvar, and fluxvar structures. These are passed in as input arguments. It also calculates values for variables in the fluxvar structure so this must be returned in the function call as an output argument. The Julia function `func` evaluates func.

# INPUTS

  * `args...`: other arguments to be passed to `func`
