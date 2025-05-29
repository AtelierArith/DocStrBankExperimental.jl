```
Varspec
```

Struct to hold all relevant information for one variable.  Fields are

  * name: name of the variable
  * storagetype: Julia type of variable
  * conversionfcie: Julia function to convert the raw string value to the Julia type, used for reading
  * dumpfcie: Julia function to convert the Julia type to a fixed width string, used for writing
  * startpos: starting position of variabele in record
  * length: length in bytes of variable

Predefined usable types are `InlineStringXX`-types for string variables, `Union{Missing,Int64}` and `IntXX` for integer variables, `FloatXX` for real numbers and `Nothing` for variables that must be skipped. If you want to use another type for input, then you must specify a function to convert the byte-string to the given type.

To write to a fixed width file, conversion functions for the used types must be available. Predefined function are defined for `String`, `Union{Missing,Int64}`, `Float64` and `Nothing`.
