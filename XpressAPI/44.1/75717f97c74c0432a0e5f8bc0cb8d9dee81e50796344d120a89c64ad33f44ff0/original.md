```
XPRSslpgetcolinfoint(prob, type, col)::info
```

Get current column information.

# Arguments

  * `prob::XPRSprob`: The current SLP problem
  * `type::Integer`: Type of information (see below)
  * `col::Integer`: Index of the column whose information is to be handled

# Return value

  * `info::Int32`: Address of information to be set or retrieved

See also the documentation of the correponding function [XPRSslpgetcolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcolinfo.html) in the C API.
