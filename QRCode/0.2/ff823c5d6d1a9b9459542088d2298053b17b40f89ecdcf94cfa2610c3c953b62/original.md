```
qrcode(message::AbstractString, eclevel = Medium(); compact = false)
```

Create a `BitArray{2}` with the encoded `message`, with `true` (`1`) for the black areas and `false` (`0`) as the white ones. If `compact` is `false`, white space is added around the QR code.

The error correction level `eclevel` can be picked from four values: `Low()` (7% of missing data can be restored), `Medium()` (15%), `Quartile()` (25%) or `High()` (30%). Higher levels make denser QR codes.
