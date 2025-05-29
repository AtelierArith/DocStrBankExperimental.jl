```
imageinqrcode( code::QRCode
             , img::AbstractMatrix{Bool}
             ; rate::Real=1
             , singlemask::Bool=true
             , leftop::Tuple{Int, Int}=(-1, -1)
             , fillalignment::Bool=false
             ) where T <: Union{Bool, Nothing}
```

QRコード内に画像をプロットします。

## 引数

  * `code::QRCode`: QRコード
  * `img::AbstractMatrix{Bool}`: プロットする画像
  * `rate::Real=1`: エラー訂正コードワードの損傷率
  * `singlemask::Bool=true`: デフォルトのマスクパターンを使用
  * `leftop::Tuple{Int,Int}=(-1, -1)`: 画像の左上隅
