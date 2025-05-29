```
modefreq(model::Plate, fmax)
modefreq(model::Membrane, fmax)
```

単純支持された長方形プレートまたはクランプされた長方形膜の自然周波数をfmaxまで計算します。

**入力**

  * `model`: プレートに関連するデータを含む構造
  * `fmax`: モード形状を計算するための最大周波数 [Hz]

**出力**

  * `ωmn`: ωmax = 2π*fmaxまで計算された自然周波数 [Hz]
  * `kmn`: モード波数の行列
