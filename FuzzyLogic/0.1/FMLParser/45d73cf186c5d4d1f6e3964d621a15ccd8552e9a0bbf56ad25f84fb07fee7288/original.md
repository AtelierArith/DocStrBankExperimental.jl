```
parse_fml(s::String)::AbstractFuzzySystem
```

Parse a fuzzy inference system from a string representation in Fuzzy Markup Language (FML).

### Inputs

  * `s::String` – string describing a fuzzy system in FML conformant to the IEEE 1855-2016 standard.

### Notes

The parsers can read FML comformant to IEEE 1855-2016, with the following remarks:

  * only Mamdani and Sugeno are supported.
  * Operators `and` and `or` definitions should be set in the rule base block. Definitions at individual rules are ignored.
  * Modifiers are not supported.
