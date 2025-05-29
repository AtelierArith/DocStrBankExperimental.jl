```
exportqrcode( message::AbstractString
            , path::AbstractString = "qrcode.png"
            ; eclevel::ErrCorrLevel = Medium()
            , version::Int = 0
            , mode::Mode = nothing
            , width::int = 4
            , pixels::Int = 160)
```

Create an image with the encoded `message` of approximate size `pixels x pixels`.

The error correction level `eclevel` can be picked from four values: `Low()` (7% of missing data can be restored), `Medium()` (15%), `Quartile()` (25%) or `High()` (30%). Higher levels make denser QR codes.

The version of the QR code can be picked from 1 to 40. If the assigned version is  too small to contain the message, the first available version is used.

The encoding mode `mode` can be picked from four values: `Numeric()`, `Alphanumeric()`, `Byte()`, `Kanji()` or `UTF8()`. If the assigned `mode` is `nothing` or failed to contain the message, the mode is automatically picked.

The mask pattern `mask` can be picked from 0 to 7. If the assigned `mask` is `nothing`, the mask pattern will picked by the penalty rules.
