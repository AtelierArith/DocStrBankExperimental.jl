```
vomps!(AL1, AR1, T, AL, AR, opts)
```

VOMPSアルゴリズムを使用したMPO-MPS積圧縮。MPOはテンソルTで表され、MPSは左および右のMPSテンソルALとARで表されます。出力はAL1とAR1に保存されます。

# 引数

  * `AL1/AR1::MPSTensor`: 更新対象の左/右MPSテンソル（インプレースで修正されます）
  * `T::MPOTensor`: MPOローカルテンソル
  * `AL/AR::MPSTensor`: MPSテンソル
  * `opts::VOMPSOptions`: アルゴリズム設定パラメータ

# 戻り値

  * `AL1/AR1::MPSTensor`: 更新された左/右MPSテンソル（インプレースで修正されます）
  * `AC1::MPSTensor`: 更新された中心ACテンソル
  * `C1::MPSBondTensor`: 更新された中心ボンドテンソル
  * `power_method_conv::Real`: 最終ゲージ固定からの収束メトリック（無効の場合はNaN）。AL1とALで表されるMPSの違いを測定します（同等のMPSの場合は= 0であるべきです）
