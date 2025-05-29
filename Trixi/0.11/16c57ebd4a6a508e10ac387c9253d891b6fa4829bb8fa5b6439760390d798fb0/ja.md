```
SubcellLimiterIDPCorrection()
```

後処理IDPリミッター[`SubcellLimiterIDP`](@ref)のための抗拡散補正ステージを[`VolumeIntegralSubcellLimiting`](@ref)と共に呼び出します。

!!! note
    このコールバックと実際のリミッター[`SubcellLimiterIDP`](@ref)は一緒に機能します。これは置き換えではなく、必要な追加です。


## 参考文献

  * Rueda-Ramírez, Pazner, Gassner (2022) 不連続ガレルキンスペクトル要素法のためのサブセル制限戦略 [DOI: 10.1016/j.compfluid.2022.105627](https://doi.org/10.1016/j.compfluid.2022.105627)
  * Pazner (2020) サブセル凸制限を用いたスパース不変領域保存不連続ガレルキン法 [DOI: 10.1016/j.cma.2021.113876](https://doi.org/10.1016/j.cma.2021.113876)
