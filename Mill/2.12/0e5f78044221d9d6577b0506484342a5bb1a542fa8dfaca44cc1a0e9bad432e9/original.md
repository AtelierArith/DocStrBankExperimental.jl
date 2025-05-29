```
Mill.string_end_code!(c::Integer; persist=false)
```

Set the new value to the `string_end_code` parameter used as a code point of the abstract string-end character to `c`. The default value of the parameter is `0x03`, which corresponds to the `ETX` character in ASCII encoding.

`c` should fit into `UInt8`.

Set `persist=true` to persist this setting between sessions.

See also: [`Mill.string_end_code`](@ref), [`Mill.string_start_code`](@ref), [`Mill.string_start_code!`](@ref).
