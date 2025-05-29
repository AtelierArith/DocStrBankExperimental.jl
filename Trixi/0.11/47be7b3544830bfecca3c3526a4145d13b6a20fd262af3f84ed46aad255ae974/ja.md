```
splitting_drikakis_tsangaris(u, orientation_or_normal_direction,
                             equations::CompressibleEulerEquations2D)
splitting_drikakis_tsangaris(u, which::Union{Val{:minus}, Val{:plus}}
                             orientation_or_normal_direction,
                             equations::CompressibleEulerEquations2D)
```

一般化座標のためのSteger-Warmingフラックスベクトル分割[`splitting_steger_warming`](@ref)の改良版。この分割は、Hänelらによるエネルギーフラックスの再定式化も行い、無粘性流れに対する全温度の保存を得る。

"マイナス"（負の軸方向に進む波に関連）と"プラス"（正の軸方向に進む波に関連）のフラックスのタプルを返します。フラックスのうち1つだけが必要な場合は、引数`which`を`Val{:minus}()`または`Val{:plus}()`に設定した関数シグネチャを使用してください。

!!! warning "実験的実装（アップウィンドSBP）"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

  * D. Drikakis and S. Tsangaris (1993) On the solution of the compressible Navier-Stokes equations using improved flux vector splitting methods [DOI: 10.1016/0307-904X(93)90054-K](https://doi.org/10.1016/0307-904X(93)90054-K)
  * D. Hänel, R. Schwane and G. Seider (1987) On the accuracy of upwind schemes for the solution of the Navier-Stokes equations [DOI: 10.2514/6.1987-1105](https://doi.org/10.2514/6.1987-1105)
