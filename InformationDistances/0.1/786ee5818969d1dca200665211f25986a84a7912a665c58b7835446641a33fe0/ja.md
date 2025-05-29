```
LibDeflateCompressor <: AbstractCompressor
```

`LibDeflate.jl`を使用して圧縮するコンプレッサーです。

---

```
LibDeflateCompressor(;compresslevel=12)
```

圧縮レベル`compresslevel`で`LibDeflateCompressor`を作成します。

# 例

```jldoctest
julia> LibDeflateCompressor()
LibDeflateCompressor(12)

julia> LibDeflateCompressor(;compresslevel=8)
LibDeflateCompressor(8)
```
