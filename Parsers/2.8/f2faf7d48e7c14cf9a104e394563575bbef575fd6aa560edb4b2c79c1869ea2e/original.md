```
PosLen(pos, len, ismissing, escaped)
```

A custom 64-bit primitive that allows efficiently storing the byte position and length of a value within a byte array, along with whether a sentinel value was parsed, and whether the parsed value includes escaped characters. Specifically, the use of 64-bits is:

  * 1 bit to indicate whether a sentinel value was encountered while parsing
  * 1 bit to indicate whether the escape character was encountered while parsing
  * 42 bits to note the byte position as an integer where a value is located in a byte array (max array size ~4.4TB)
  * 20 bits to note the length of a parsed value (max length of ~1MB)

These individual "fields" can be retrieved via dot access, like `PosLen.missingvalue`, `PosLen.escapedvalue`, `PosLen.pos`, `PosLen.len`.

`Parsers.xparse(String, buf, pos, len, opts)` returns `Parsers.Result{PosLen}`, where the `x.val` is a `PosLen`.
