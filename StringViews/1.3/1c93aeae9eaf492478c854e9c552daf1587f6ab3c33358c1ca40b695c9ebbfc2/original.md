```
StringView{T<:AbstractVector{UInt8}} <: AbstractString
```

`StringView(array)` creates an `AbstractString` representation of any `array` of `UInt8` data, interpreted as UTF-8 encoded Unicode. It does *not* make a copy of or modify `array`.

`StringView(buf::IOBuffer)` returns a string view of the current contents of the `buf`, equivalent to `String(take!(buf))` but without making a copy.   `StringView(buf::IOBuffer, range)` is a view of the bytes `range` (defaults to `1:position(buf)-1`) in the buffer.
