## `score` (Agatston)

```julia
score(vol, spacing, alg::Agatston; kV=120, min_size_mm=1)
score(vol, spacing, mass_cal_factor, alg::Agatston; kV=120, min_size_mm=1)
```

従来のAgatstonスコアリング技術に従ってカルシウムスコアを計算します。これは[元の論文](10.1016/0735-1097(90)90282-T)に概説されています。エネルギー（`kV`）特有の`threshold`は、以前の[出版物](https://doi.org/10.1093/ehjci/jey019)に基づいて決定されます。また、提供された場合は、`mass_cal_factor`を介してAgatstonスコアをカルシウム質量スコアに変換します。

#### 入力

  * `vol`: 興味のある領域のみを含む入力ボリューム
  * `spacing`: 知られているピクセル/ボクセル間隔
  * `alg::Agatston`: Agatstonスコアリングアルゴリズム `Agatston()`
  * `mass_cal_factor`: （オプション）計算された質量をキャリブレーションするための係数
  * kwargs:

      * `kV=120`: 入力CTスキャン画像のエネルギー
      * `min_size=1`: 最小接続成分サイズ（[`label_components`](https://github.com/JuliaImages/Images.jl)を参照）

#### 戻り値

  * `agatston_score`: 総Agatstonスコア
  * `volume_score`: Agatstonスコアリングによる総カルシウムボリューム
  * `abs_mass_score`: （オプション）キャリブレーション後の総カルシウム質量、`mass_cal_factor`が提供された場合のみ返されます

#### 参考文献

[超高速コンピュータトモグラフィーを用いた冠動脈カルシウムの定量化](https://doi.org/10.1016/0735-1097(90)90282-t)

[新しいスコアリング閾値を用いた超低線量冠動脈カルシウムスコアリング—パイロットスタディ](https://doi.org/10.1093/ehjci/jey019)
