```
exportqrcode( msgs::AbstractVector{<:AbstractString}
            , path::AbstractString = "qrcode.gif"
            ; eclevel::ErrCorrLevel = Medium()
            , version::Int = 0
            , mode::Mode = Numeric()
            , mask::Int = -1
            , width::Int = 4
            , targetsize::Int = 5
            , pixels::Int = 160
            , fps::Int = 2)
```

Create an animated gif with `msgs` of approximate size `pixels x pixels`.

The frame rate `fps` is the number of frames per second.
