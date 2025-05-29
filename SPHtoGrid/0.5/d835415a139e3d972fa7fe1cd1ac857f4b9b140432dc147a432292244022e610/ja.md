```
convert_Pnu_map_to_mJy_beam(map::Matrix{<:Real}, 
                            d_pixel::Real,
                            beam::Union{Real, Unitful.AbstractQuantity}, 
                            c::Cosmology.AbstractCosmology, 
                            z::Real)
```

[W / Hz]から[mJy / beam]へのマップを円形ビームのために変換します。

## パラメータ:

  * `map`: [W / Hz]の元のマップ。
  * `d_pixel`: $kpc$でのピクセルのサイズ。
  * `beam`: $arcmin$でのビームの半径。
  * `c`: 変換に使用される宇宙論。
  * `z`: 画像の赤方偏移。
