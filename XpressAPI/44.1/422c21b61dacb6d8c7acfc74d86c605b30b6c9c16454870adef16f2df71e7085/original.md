```
XPRSslpfixpenalties(prob)::status
```

Fixe the values of the error vectors

# Arguments

  * `prob::XPRSprob`: The current SLP problem.

# Return value

  * `status::Int32`: Return status after fixing the penalty variables: 0 is successful, nonzero otherwise.

See also the documentation of the correponding function [XPRSslpfixpenalties](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpfixpenalties.html) in the C API.
