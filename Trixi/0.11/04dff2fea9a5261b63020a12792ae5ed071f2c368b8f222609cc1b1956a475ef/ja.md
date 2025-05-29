```
splitting_coirier_vanleer(u, orientation::Integer,
                          equations::CompressibleEulerEquations1D)
splitting_coirier_vanleer(u, which::Union{Val{:minus}, Val{:plus}}
                          orientation::Integer,
                          equations::CompressibleEulerEquations1D)
```

コイリエとヴァン・リールによる圧縮性オイラー流束の分割。この分割には、圧力分割および質量とエネルギー流束成分における修正項が含まれています。これらの修正の動機は、低マッハ数制限での流れを扱うことです。

負の軸方向に進む波に関連する「マイナス」と、正の軸方向に進む波に関連する「プラス」の流束のタプルを返します。流束のうちの1つだけが必要な場合は、引数 `which` を `Val{:minus}()` または `Val{:plus}()` に設定した関数シグネチャを使用してください。

!!! warning "実験的実装 (アップウィンドSBP)"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


## 参考文献

  * William Coirier and Bram van Leer (1991) Numerical flux formulas for the Euler and Navier-Stokes equations. II - Progress in flux-vector splitting [DOI: 10.2514/6.1991-1566](https://doi.org/10.2514/6.1991-1566)
