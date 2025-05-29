```
Minuit(fcn, x0...; grad=nothing, error=(), errordef=1.0, names=(), limits=(), fixed=(), method=:migrad, maxfcn=0, 
            tolerance=0.1, precision=nothing, strategy=1, kwargs...)
```

Initialize a Minuit object.

This does not start the minimization or perform any other work yet. Algorithms  are started by calling the corresponding methods.

## Arguments

  * `fcn::Union{Function,CostFunction}` : Function to minimize. See notes for details on what kind of functions are accepted.
  * `x0::AbstractArray` : Starting values for the minimization. See notes for details on how to set starting values.
  * `grad::Union{Function,Nothing, Bool}` : If `grad` is a function, it must be a function that calculates the gradient and returns an iterable object with one entry for each parameter, which is the derivative of `fcn` for that parameter. If `nothing` (default), Minuit will use the gradient of the provided  cost function. If it does not exists Minuit will compute the gradient numerically. If `grad` is `false`, Minuit will not use the gradient.
  * `error::AbstractArray` : Starting values for the errors of the parameters. If not provided, Minuit will use 0.1 for all parameters.
  * `errordef::Real` : Error definition of the function. Minuit defines parameter errors as the change in parameter  value required to change the function value by `errordef`. Normally, for chisquared fits it is 1, and for negative log likelihood, its value is 0.5. If the user wants instead the 2-sigma errors for chisquared fits, it becomes 4, as `Chi2(x+n*sigma) = Chi2(x) + n*n`.
  * `names::Vector{String}` : Names of the parameters. If not provided, Minuit will try to extract the names from the function signature.
  * `limits::AbstractArray` : Limits for the parameters. If not provided, Minuit will use no limits for all parameters.
  * `fixed::AbstractArray` : Fixed status of the parameters. If not provided, Minuit will use `false` for all parameters. The limits are a tuple of two values, the lower and upper limit. If the parameter is fixed, the limits are set to `(-Inf, Inf)`.
  * `method::Symbol` : The minimization algorithm to use. Possible values are `:migrad`, `:simplex`
  * `maxfcn::Int` : Maximum number of function calls. If set to 0, Minuit will use a default value.
  * `tolerance::Real` : Tolerance for the minimization. If set to 0, Minuit will use a default value.
  * `kwargs` : Additional keyword arguments. Starting values for the minimization as keyword arguments. See notes for details on how to set starting values.

## Notes

### Function to minimize

By default, Minuit assumes that the callable `fcn` behaves like chi-square function, meaning that the function minimum in repeated identical random experiments is chi-square distributed up to an arbitrary additive constant. This is important for the correct error calculation. If `fcn` returns a log-likelihood, one should multiply the result with -2 to adapt it. If the function returns the negated log-likelihood, one can alternatively set the attribute `errordef` to make Minuit calculate errors properly.

Minuit reads the function signature of `fcn` to detect the number and names of the function parameters. Two kinds of function signatures are understood.

a.  Function with positional arguments.

The function has positional arguments, one for each fit parameter. Example:

```
fcn(a, b, c) =  ...
```

The parameters a, b, c must accept a real number Minuit automatically detects the parameters names in this case.

b.  Function with arguments passed as a single AbstractArray.

The function has a single argument which is an AbstractArray. Example:

```
function fcn_v(x) =  ...
```

To use this form, starting values (`x0`) needs to be passed to Minuit in form of a `Tuple` or `Vector`. In some cases, the detection may fail, and will be necessary to use the `names` keyword to set the parameter names.

### Parameter initialization

Initial values for the minimization can be set with positional arguments or via keywords. This is best explained through an example:

```
fcn(x, y) =  (x - 2)^2 + (y - 3)^2
```

The following ways of passing starting values are equivalent:

```
Minuit(fcn, x=1, y=2)
Minuit(fcn, y=2, x=1) # order is irrelevant when keywords are used ...
Minuit(fcn, [1,2])    # ... but here the order matters
```

Positional arguments can also be used if the function has no signature:

```
fcn_no_sig(args...) =  ...
Minuit(fcn_no_sig, [1,2])
```

If the arguments are explicitly named with the `names` keyword described further below, keywords can be used for initialization:

```
Minuit(fcn_no_sig, x=1, y=2, names=("x", "y"))  # this also works
```

If the function accepts a single AbstractVector, then the initial values must be passed as a single array-like object:

```
fcn_v(x) = return (x[1] - 2) ** 2 + (x[2] - 3) ** 2
Minuit(fcn_v, (1, 2))
```

Setting the values with keywords is not possible in this case. Minuit deduces the number of parameters from the length of the initialization sequence.
