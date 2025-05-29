```
LibDeflateCompressor <: AbstractCompressor
```

A compressor that uses a `LibDeflate.jl` for compressing.

---

```
LibDeflateCompressor(;compresslevel=12)
```

Create a `LibDeflateCompressor` with compression level `compresslevel`.

# Examples

```jldoctest
julia> LibDeflateCompressor()
LibDeflateCompressor(12)

julia> LibDeflateCompressor(;compresslevel=8)
LibDeflateCompressor(8)
```
