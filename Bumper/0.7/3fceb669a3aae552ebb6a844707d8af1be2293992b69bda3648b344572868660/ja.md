```
with_buffer(f, buf)
```

関数 `f()` を、`default_buffer()` が通常の `default_buffer` の代わりに `buf` を返すコンテキストで実行します。これは現在、`SlabBuffer{1_048_576}` と `AllocBuffer{Vector{UInt8}}` のみで機能します。

例:

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
