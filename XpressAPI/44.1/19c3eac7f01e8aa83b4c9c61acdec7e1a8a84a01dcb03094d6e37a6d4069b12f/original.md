```
XPRSaddsetnames(prob, names, first, last)::prob
```

When a model with MIP entities is loaded, any special ordered sets may not have names associated with them.

If you wish names to appear in the ASCII solutions files, the names for a range of sets can be added with this function.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `names::AbstractVector{AbstractString}`: Character buffer containing the null-terminated string names.
  * `first::Integer`: Start of the range of sets.
  * `last::Integer`: End of the range of sets.

# Return value

  * `prob::XPRSprob`: The current problem.

See also the documentation of the correponding function [XPRSaddsetnames](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddsetnames.html) in the C API.
