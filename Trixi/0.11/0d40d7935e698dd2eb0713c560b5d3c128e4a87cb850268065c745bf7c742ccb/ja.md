```
splitting_steger_warming(u, orientation::Integer,
                         equations::CompressibleEulerEquations2D)
splitting_steger_warming(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation::Integer,
                         equations::CompressibleEulerEquations2D)
```

StegerとWarmingの圧縮性オイラー流束の分割。曲線座標の場合は、改良されたSteger-Warming型分割[`splitting_drikakis_tsangaris`](@ref)を使用してください。

流束のタプル「マイナス」（負の軸方向に進む波に関連）と「プラス」（正の軸方向に進む波に関連）を返します。流束のうち1つだけが必要な場合は、引数`which`を`Val{:minus}()`または`Val{:plus}()`に設定した関数シグネチャを使用してください。

!!! warning "実験的実装（アップウィンドSBP）"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

  * Joseph L. StegerとR. F. Warming (1979) 無粘性ガス動力学方程式の流束ベクトル分割と有限差分法への応用 [NASA技術覚書](https://ntrs.nasa.gov/api/citations/19790020779/downloads/19790020779.pdf)
