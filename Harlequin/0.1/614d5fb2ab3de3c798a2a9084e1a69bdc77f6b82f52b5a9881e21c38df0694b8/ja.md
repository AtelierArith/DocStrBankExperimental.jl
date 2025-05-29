```
gaussian_beam(res::Healpix.Resolution, angle_std_rad; normalization = 1.0) where {T,O <: Healpix.Order}
gaussian_beam(nside::Integer, angle_std_rad; normalization = 1.0) where {T,O <: Healpix.Order}
```

円形ガウスビームのマップを `beam_map` に保存します。ビームの幅は、ラジアンで表現されるパラメータ `angle_std_rad` を通じて提供されます。代わりにFWHMを指定したい場合は、次の例のように `fwhm2std` を使用してください：

```julia
# FWHMが2.5°であると仮定
beam_map = gaussian_beam(1024, 2.5 |> fwhm2std)
```

`gaussian_beam!` も参照してください。
