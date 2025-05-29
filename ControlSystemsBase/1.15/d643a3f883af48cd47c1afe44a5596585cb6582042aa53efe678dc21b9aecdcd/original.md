```
gram(sys, opt; kwargs...)
```

Compute the grammian of system `sys`. If `opt` is `:c`, computes the controllability grammian. If `opt` is `:o`, computes the observability grammian.

See also [`grampd`](@ref) For keyword arguments, see [`grampd`](@ref).

# Extended help

Note: Gramian computations are sensitive to input-output scaling. For the result of a numerical balancing, gramian computation or truncation of MIMO systems to be meaningful, the inputs and outputs of the system must thus be scaled in a meaningful way. A common (but not the only) approach is:

  * The outputs are scaled such that the maximum allowed control error, the maximum expected reference variation, or the maximum expected variation, is unity.
  * The input variables are scaled to have magnitude one. This is done by dividing each variable by its maximum expected or allowed change, i.e., $u_{scaled} = u / u_{max}$

Without such scaling, the result of balancing will depend on the units used to measure the input and output signals, e.g., a change of unit for one output from meter to millimeter will make this output 1000x more important.
