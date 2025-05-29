@handlemissings_any(fun, ...)

Calling [`handlemissings`](@ref) with defaults tailored to an original method where the  eltype accepts missings already:

  * Dispatching methods as with [`@handlemissings_stub`](@ref)
  * Agument type of the new function defaults to `Any`. No default method (without the `MissingStragety` argument) is created.
  * PassMissing methods calls the original directly without converting the type of the  argument with missings ([`mgen.passmissing_nonconvert`](@ref)).
  * HandleMissing methods calls the original directly with the `skipmissing()`  iterator object ([`mgen.handlemissing_skip`](@ref)).

Arguments: see [`handlemissings`](@ref)    

Note, that if the original method allows `missing` in `eltype`, you need to explicitly pass the `PassMissing()` by argument. A potential default method would override the original method and either not be called at all or call itself recursively causing an infinite loop.
