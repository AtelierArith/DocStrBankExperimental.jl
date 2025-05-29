```
XPRSmsaddpreset(prob, description, preset, maxjobs, data)::prob
```

Loads a preset of jobs into the multistart job pool.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `description::Union{Nothing,AbstractString}`: Text description of the preset.
  * `preset::Integer`: Which preset to load.
  * `maxjobs::Integer`: Maximum number of jobs to be added to the multistart pool.
  * `data::Any`: Job specific user context pointer to be passed to the multistart callbacks.

# Return value

  * `prob::XPRSprob`: The current SLP problem.

See also the documentation of the correponding function [XPRSmsaddpreset](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmsaddpreset.html) in the C API.
