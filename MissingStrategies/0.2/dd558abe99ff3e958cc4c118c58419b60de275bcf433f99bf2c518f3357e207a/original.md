```
getdispatchinfo(...)
```

Collect information for dispatching non-missing types into a dictionary.

# Arguments

see [`handlemissings`](@ref).

# Return value

A dictionary with entries   

  * `dict_forig`: dictionary result of MacroTools.splitdef(fun)
  * `fname_disp`: Symbol of the dispatch function name,
  * `argnames`: the aguement names of fun,
  * `kwargpasses`: an Vector of expression of keyword parameters 'argname = argname'
  * `pos_missing`: position of the argument that should handle missings,
  * `type_missing`: the new type of that argument,
  * `pos_strategy`: the position at which the argument of MissingStrategy is inserted,
  * `defaultstrategy`: the default of that argument of type [`MissingStrategy`](@ref)
  * `suffix="_hm"`: number to be appended to `fname_disp` to avoid method ambiguities,

These match the required argument for the method generators in module [`mgen`](@ref).
