```
parse_fcl(s::String)::AbstractFuzzySystem
```

Parse a fuzzy inference system from a string representation in Fuzzy Control Language (FCL).

### Inputs

  * `s::String` – string describing a fuzzy system in FCL conformant to the IEC 1131-7 standard.

### Notes

The parsers can read FCL comformant to IEC 1131-7, with the following remarks:

  * Sugeno (system with singleton outputs) shall use COGS as defuzzifier.
  * the `RANGE` keyword is required for both fuzzification and defuzzification blocks.
  * Only the required `MAX` accumulator is supported.
  * Default value for defuzzification not supported.
  * Optional local variables are not supported.

With the exceptions above, the parser supports all required and optional features of the standard (tables 6.1-1 and 6.1-2). In addition, it also supports the following features:

  * Piecewise linear functions can have any number of points.
  * Membership degrees in piecewise linear functions points can be any number between $0$ and $1$.
