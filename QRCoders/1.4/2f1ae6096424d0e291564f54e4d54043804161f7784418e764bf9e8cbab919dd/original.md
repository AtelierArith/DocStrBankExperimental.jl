```
qrcode( message::AbstractString
      ; eclevel::ErrCorrLevel = Medium()
      , version::Int = 0
      , mode::Mode = Numeric()
      , mask::Int = -1
      , width::Int=0)
```

Create a `BitArray{2}` with the encoded `message`, with `true` (`1`) for the black areas and `false` (`0`) as the white ones.

The error correction level `eclevel` can be picked from four values: `Low()` (7% of missing data can be restored), `Medium()` (15%), `Quartile()` (25%) or `High()` (30%). Higher levels make denser QR codes.

The version of the QR code can be picked from 1 to 40. If the assigned version is  too small to contain the message, the first available version is used.

The encoding mode `mode` can be picked from five values: `Numeric()`, `Alphanumeric()`, `Byte()`, `Kanji()` or `UTF8()`. If the assigned `mode` is `nothing` or failed to contain the message, the mode is automatically picked.

The mask pattern `mask` can be picked from 0 to 7. If the assigned `mask` is `nothing`, the mask pattern will picked by the penalty rules.
