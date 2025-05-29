Struct describing parameters for injecting NaNs

## Fields

  * `active::Boolean` inject only if true
  * `value::Any` what value to inject; typically `NaN` or `Inf`
  * `n_inject::Int` maximum number of NaNs to inject; gets decremented every time a NaN gets injected
  * `odds::Int` inject a NaN with 1:odds probability—higher value → rarer to inject
  * `functions::Array{FunctionRef}` if given, only inject NaNs when within these functions; default is to not discriminate on functions
  * `libraries::Array{String}` if given, only inject NaNs when within this library.

    **NOTE**: Libraries MUST NOT have a `.jl` suffix—we strip out that suffix when looking for the name of a library by default, so don't include it here otherwise it will never match.
  * `record::String` if given, record injection invents in a way that can be replayed later with the `replay` argument.
  * `replay::String` if given, ignore all previous directives and use this file for injection replay.

`functions` and `libraries` work together as a union: i.e. the set of possible NaN injection points is a union of the places matched by `functions` and `libraries`.
