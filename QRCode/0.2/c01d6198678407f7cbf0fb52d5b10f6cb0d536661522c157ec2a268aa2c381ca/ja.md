```
getversion(message::AbstractString, mode::Mode, level::ErrCorrLevel)
```

QRコードのバージョンを返します。1から40の間です。

```jldoctest
julia> getversion("Hello World!", Alphanumeric(), High())
2
```
