```
XPRSsetdefaults(prob)::prob
```

Sets all controls to their default values.

Must be called before the problem is read or loaded by XPRSreadprob, XPRSloadmip, XPRSloadlp, XPRSloadmiqp, XPRSloadqp.

# Arguments

  * `prob::XPRSprob`: The current problem.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSsetdefaults](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetdefaults.html) in the C API.
