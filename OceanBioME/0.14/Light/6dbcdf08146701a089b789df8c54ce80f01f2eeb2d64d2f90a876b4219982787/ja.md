```
MultiBandPhotosyntheticallyActiveRadiation(; grid::AbstractGrid{FT}, 
                                             bands = ((400, 500), (500, 600), (600, 700)), #nm
                                             base_bands = MOREL_λ,
                                             base_water_attenuation_coefficient = MOREL_kʷ,
                                             base_chlorophyll_exponent = MOREL_e,
                                             base_chlorophyll_attenuation_coefficient = MOREL_χ,
                                             field_names = [par_symbol(n, length(bands)) for n in 1:length(bands)],
                                             surface_PAR = default_surface_PAR)
```

`surface_PAR`を`surface_PAR_division`で`bands`に分割した`MultiBandPhotosyntheticallyActiveRadiation`減衰モデルを返します。

減衰morel*coefficientsは、`base*water*attenuation*coefficient`、`base*chlorophyll*exponent`、および`base*chlorophyll*attenuation*coefficient`から計算され、これらは`base*bands`の波長での係数の配列である必要があります。

返される`field_names`はデフォルトで`PAR₁`、`PAR₂`などになりますが、ユーザーによって指定することもできます。

# キーワード引数

  * `grid`: モデルを構築するためのグリッド
  * `water_red_attenuation`、...、`phytoplankton_chlorophyll_ratio`: パラメータ値
  * `surface_PAR`: 表面での光合成可能な放射線のための関数（または将来的には配列）、これは`f(x, y, t)`である必要があり、`x`と`y`はネイティブ座標（すなわち、直交グリッドの場合はメートル、適切な場合は緯度/経度）です。
