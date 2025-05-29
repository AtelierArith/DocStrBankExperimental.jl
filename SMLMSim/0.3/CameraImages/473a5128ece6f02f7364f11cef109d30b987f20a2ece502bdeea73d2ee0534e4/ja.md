```
gen_image(smld::SMLD, psf::AbstractPSF, frame::Int; kwargs...) -> Matrix{T} where T<:Real
```

SMLDデータから特定のフレームの単一カメラ画像を生成します。パラメータの完全なドキュメントについては`gen_images`を参照してください。

# 戻り値

  * エミッタの光子の型に一致するMatrix{T}としての2Dカメラ画像
