```
Mill.string_start_code!(c::Integer; persist=false)
```

Set the new value to the `string_start_code` parameter used as a code point of the abstract string-start character to `c`. The default value of the parameter is `0x02`, which corresponds to the `STX` character in ASCII encoding.

`c` should fit into `UInt8`.

Set `persist=true` to persist this setting between sessions.

See also: [`Mill.string_start_code`](@ref), [`Mill.string_end_code`](@ref), [`Mill.string_end_code!`](@ref).
