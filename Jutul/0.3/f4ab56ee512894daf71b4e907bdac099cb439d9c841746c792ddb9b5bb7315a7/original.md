```
get_ad_entity_scalar(v::Real, npartials, diag_pos = nothing; <keyword_arguments>)
```

Get scalar with partial derivatives as AD instance.

# Arguments

  * `v::Real`: Value of AD variable.
  * `npartials`: Number of partial derivatives each AD instance holds.
  * `diag_pos` = nothing: Position(s) of where to set 1 as the partial derivative instead of zero.

# Keyword arguments

  * `tag = nothing`: Tag for AD instance. Two AD values of the different tag cannot interoperate to avoid perturbation confusion (see ForwardDiff documentation).
