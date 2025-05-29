```
splitting_steger_warming(u, orientation::Integer,
                         equations::CompressibleEulerEquations1D)
splitting_steger_warming(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation::Integer,
                         equations::CompressibleEulerEquations1D)
```

StegerとWarmingの圧縮性オイラー流束の分割。

負の軸方向に進む波に関連する「マイナス」と、正の軸方向に進む波に関連する「プラス」の流束のタプルを返します。流束のうち1つだけが必要な場合は、引数`which`を`Val{:minus}()`または`Val{:plus}()`に設定した関数シグネチャを使用してください。

!!! warning "実験的実装 (アップウィンドSBP)"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

  * Joseph L. Steger and R. F. Warming (1979) Flux Vector Splitting of the Inviscid Gasdynamic Equations With Application to Finite Difference Methods [NASA Technical Memorandum](https://ntrs.nasa.gov/api/citations/19790020779/downloads/19790020779.pdf)
