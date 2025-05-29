```
exportqrcode( codes::AbstractVector{QRCode}
            , path::AbstractString = "qrcode.gif"
            ; pixels::Int = 160
            , fps::Int = 2)
```

Create an animated gif with `codes` of approximate size `targetsize`.

The frame rate `fps` is the number of frames per second.

Note: The `codes` should have the same size while the other properties can be different.
