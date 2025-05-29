```
exportqrcode( message::AbstractString
            , path = "qrcode.png"
            , eclevel = Medium()
            ; targetsize = 5
            , compact = false )
```

Create a `PNG` file with the encoded `message` of approximate size `targetsize` cm. If `compact` is `false`, white space is added around the QR code.

The error correction level `eclevel` can be picked from four values: `Low()` (7% of missing data can be restored), `Medium()` (15%), `Quartile()` (25%) or `High()` (30%). Higher levels make denser QR codes.
