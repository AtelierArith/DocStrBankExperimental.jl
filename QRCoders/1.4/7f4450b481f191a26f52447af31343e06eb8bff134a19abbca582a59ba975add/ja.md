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

`msgs`を使用して、約`pixels x pixels`のサイズのアニメーションGIFを作成します。

フレームレート`fps`は、1秒あたりのフレーム数です。
