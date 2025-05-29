```
XPRSmsaddcustompreset(prob, description, preset, maxjobs, ninitial, colind, initial, nintcontrols, intcontrolid, intcontrolval, ndblcontrols, dblcontrolid, dblcontrolval, data)::prob
```

A combined version of XSLPmsaddjob and XSLPmsaddpreset.

The preset described is loaded, topped up with the specific settings supplied

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `description::Union{Nothing,AbstractString}`: Text description of the job.
  * `preset::Integer`: Which preset to load.
  * `maxjobs::Integer`: Maximum number of jobs to be added to the multistart pool.
  * `ninitial::Integer`: Number of initial values to set.
  * `colind::AbstractVector{Integer}`: Indices of the variables for which to set an initial value.
  * `initial::AbstractVector{Number}`: Initial values for the variables for which to set an initial value.
  * `nintcontrols::Integer`: Number of integer controls to set.
  * `intcontrolid::AbstractVector{Integer}`: The indices of the integer controls to be set.
  * `intcontrolval::AbstractVector{Integer}`: The values of the integer controls to be set.
  * `ndblcontrols::Integer`: Number of double controls to set.
  * `dblcontrolid::AbstractVector{Integer}`: The indices of the double controls to be set.
  * `dblcontrolval::AbstractVector{Number}`: The values of the double controls to be set.
  * `data::Any`: Job specific user context pointer to be passed to the multistart callbacks.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSmsaddcustompreset](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmsaddcustompreset.html) in the C API.
