```
FCN(fnc, grad=nothing, arraycall=false, errordef=1.0)
```

Create a JuliaFcn object from a Julia function `fnc` and its gradient `grad`.

## Arguments

  * `fnc::Function` : The Julia function to minimize. It can either accept a set of discrete arguments or a single argument of type `AbstractVector`.   This is decided in conjunction with the argument `arraycall`.
  * `grad::Function=nothing`; Gradient Julia function. The input arguments follow the same as for `fcn` and it returns a `Vector`, of length the number of parameters, with the gradients.
  * `arraycall::Bool=false` : If `true`, the function `fcn` accepts a single argument of type `AbstractVector`. If `false`, the function accepts a set of discrete arguments.
  * `errordef::Real=1.0` : Error definition of the function. Minuit defines parameter errors as the change in parameter   value required to change the function value by `errordef`. Normally, for chisquared fits it is 1, and for negative log likelihood, its value is 0.5.

## Returns

  * `JuliaFcn` : A JuliaFcn object inheriting from the abstract C++ class `Minuit::FCNBase`that can be used in Minuit.

## Usage

```julia
fcn(x, y) = (x - 2)^2 + (y - 3)^2
grad(x, y) = [2*(x - 2), 2*(y - 3)]
jf = FCN(fcn, grad)

jf(1.0, 1.0)  # returns 5.0
jf.grad(1.0, 1.0)  # returns [-2.0, -4.0]

jf.nfcn # returns the number of function calls
jf.ngrad # returns the number of gradient calls

jf.has_gradient # returns true
```
