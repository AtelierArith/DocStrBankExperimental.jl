```
getversion(message::AbstractString, mode::Mode, level::ErrCorrLevel)
```

Return the version of the QR code, between 1 and 40.

```jldoctest
julia> getversion("Hello World!", Alphanumeric(), High())
2
```
