```
isinplace(f, inplace_param_number, fname = "f", iip_preferred = true;
          has_two_dispatches = true,
          outofplace_param_number = inplace_param_number - 1)
isinplace(f::AbstractSciMLFunction[, inplace_param_number])
```

Check whether a function operates in place by comparing its number of arguments to the expected number. If `f` is an `AbstractSciMLFunction`, then the type parameter is assumed to be correct and is used. Otherwise `inplace_param_number` is checked against the methods table, where `inplace_param_number` is the number of arguments for the in-place dispatch. The out-of-place dispatch is assumed to have `outofplace_param_number` parameters (one less than the inplace version by default). If neither of these dispatches exist, an error is thrown. If the error is thrown, `fname` is used to tell the user which function has the incorrect dispatches.

`iip_preferred` means that if `inplace_param_number=4` and methods of both 3 and for 4 args exist, then it will be chosen as in-place. `iip_dispatch` flips this decision.

If `has_two_dispatches = false`, then it is assumed that there is only one correct dispatch, i.e. `f(u,p)` for OptimizationFunction, and thus the check for the oop form is disabled and the 2-argument signature is ensured to be matched.

# See also

  * [`numargs`](@ref numargs)
