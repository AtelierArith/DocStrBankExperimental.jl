```
groebner_apply!(trace, polynomials; options...)
groebner_apply!(trace, batch::NTuple{N, Vector}; options...)
```

Computes a Groebner basis of the ideal generated by `polynomials` following the given `trace`. 

See also `groebner_learn`.

## Arguments

  * `trace`: a trace produced by `groebner_learn`.
  * `polynomials`: an array of polynomials. Must be polynomials from   AbstractAlgebra.jl or Nemo.jl over `GF(p)` or `Nemo.GF(p)`. It is possible   to supply a tuple of `N` arrays of polynomials to compute `N` Groebner bases   simultaneously. This could be more efficient overall than computing them in   separate.

## Returns

Returns a tuple (`success`, `basis`).

  * `success`: a bool, whether the call succeeded.
  * `basis`: an array of polynomials, a Groebner basis.

## Possible Options

The `groebner_apply!` function automatically inherits most parameters from the given `trace`.

## Example

For examples, see the documentation of `groebner_learn`.

## Notes

  * In general, `success` may be a false positive. The probability of a false positive is considered to be low enough in some practical applications.
  * This function is **not** thread-safe since it mutates `trace`.
  * This function is **not** safe against program interruptions. For example,   pressing `Ctrl + C` while `groebner_apply!(trace, ...)` is running may leave   `trace` corrupted.
