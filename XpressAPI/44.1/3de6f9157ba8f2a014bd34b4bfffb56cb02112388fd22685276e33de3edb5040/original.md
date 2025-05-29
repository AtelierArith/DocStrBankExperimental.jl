```
XPRSnlpgetformula(prob, row, parsed, maxtypes, type, value)::ntypes, type, value
```

Retrieve a single matrix formula as a formula split into tokens.

# Arguments

  * `prob::XPRSprob`: The current SLP problem.
  * `row::Integer`: Integer holding the row index for the formula.
  * `parsed::Integer`: Integer indicating whether the formula of the row is to be returned in internal unparsed format (`parsed`=0) or parsed (reverse Polish) format (`parsed`=1).
  * `maxtypes::Integer`: Maximum number of tokens to return, i.e., the length of the type and value arrays.
  * `type::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: Integer array to hold the token types for the formula. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.
  * `value::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: Double array of values corresponding to `type`. You may pass `XPRS_ALLOC` for this argument to have the function allocate an array of appropriate size for you. You may pass `nothing` for this argument to not query that information.

# Return values

  * `ntypes::Int32`: Will be set to the length of the formula, including the `XSLP_EOF` token.
  * `type::Union{Nothing,AbstractVector{Int32}}`: Integer array to hold the token types for the formula.
  * `value::Union{Nothing,AbstractVector{Float64}}`: Double array of values corresponding to `type`.

See also the documentation of the correponding function [XPRSnlpgetformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformula.html) in the C API.
