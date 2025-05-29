```
with_buffer(f, buf)
```

Execute the function `f()` in a context where `default_buffer()` will return `buf` instead of the normal `default_buffer`. This currently only works with `SlabBuffer{1_048_576}`, and `AllocBuffer{Vector{UInt8}}`.

Example:

```
julia> let b1 = default_buffer()
           b2 = SlabBuffer()
           with_buffer(b2) do
               @show default_buffer() == b2
           end
           @show default_buffer() == b1
       end
default_buffer() == b2 = true
default_buffer() == b1 = true
true
```
