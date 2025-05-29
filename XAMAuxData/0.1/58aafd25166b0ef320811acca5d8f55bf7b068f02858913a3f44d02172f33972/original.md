```
Error
```

Enum type representing errors returned when loading invalid auxiliary data values. The errors are *nonexhausitve* - more might be added in a non-breaking release.

The following errors may contained in `AbstractAuxiliary` instead of the real value:

  * `InvalidTypeTag` (SAM only): An aux value with an unknown type
  * `InvalidArrayEltype` (SAM only): A `B` value with an unknown element type
  * `InvalidInt` (SAM only): An integer that can't be parsed to an `Int32`
  * `InvalidFloat` (SAM only): A float that can't be parsed to a `Float32`
  * `InvalidChar`: Loading a `Char` not in `'!':'~'`
  * `InvalidString`: A string that contains a character not in `re"[ !-~]"`
  * `InvalidHex`: a `H` value with an odd number of symbols, or symbol not in `re"[0-9A-F]"`
  * `InvalidArray`: A malformed `B` value

See also: [`Errors`](@ref)
