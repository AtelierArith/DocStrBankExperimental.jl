```
load_fits(fitsfile::String, T::Type{<:IntensityMap}))
```

これは、EHTのさまざまな画像処理アルゴリズムに対してより堅牢なfitsファイルを読み込みます。すなわち、clean、smili、eht-imagingで動作します。この関数は`T<:IntensityMap`を返します。デフォルトでは、`T===IntensityMap`の場合、Stokes I画像のみを返します。`T<:IntensityMap{StokesParams}`の場合、完全なStokes画像を返します。
