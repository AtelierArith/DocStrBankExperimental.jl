```
convert_Pnu_map_to_mJy_beam(map::Matrix{<:Real}, 
                            d_pixel::Real,
                            beam::Union{T, Vector{T}}, 
                            h::AbstractGadgetHeader) where T::Union{Real, Unitful.AbstractQuantity}
```

[Gadgetヘッダー](https://example.com)を使用して、単位を[W / Hz]から[mJy / beam]に変換します。

## パラメータ:

  * `map`: [W / Hz]の元のマップ。
  * `d_pixel`: $kpc$におけるピクセルのサイズ。
  * `beam`: $arcmin$におけるビームの半径/寸法。
  * `h`: シミュレーションのGadgetヘッダー。
