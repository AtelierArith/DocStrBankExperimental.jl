```
find_newlines!(l::Lexer, buf::Vector{UInt8}, out::AbstractVector{Int32}, curr_pos::Int=firstindex(buf), end_pos::Int=lastindex(buf))
```

Find newlines in `buf[curr_pos:end_pos]` and push their positions to `out`. The newline positions are relative to the beginning of `buf`. The type of the `Lexer` determines the rules for handling quotes and escapes. See `Lexer` for details.

`end_pos` must be less than `typemax(Int32)` and `1 <= curr_pos <= end_pos`.
