```
exportqrcode( codes::AbstractVector{QRCode}
            , path::AbstractString = "qrcode.gif"
            ; pixels::Int = 160
            , fps::Int = 2)
```

`codes`の近似サイズ`targetsize`でアニメーションGIFを作成します。

フレームレート`fps`は、1秒あたりのフレーム数です。

注意: `codes`は同じサイズである必要がありますが、他のプロパティは異なっていても構いません。
