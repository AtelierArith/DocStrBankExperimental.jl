```
getPriorParameters()
```

これらは、カーネルパラメータ、交絡因子構造の共分散ノイズ、および交絡因子のガウス事前共分散に対する逆ガンマ事前のスケールと形状の標準値です。

  * `uNoiseShape::Float64=4.0`: Uのノイズに対するInvGamma事前の形状
  * `uNoiseScale::Float64=4.0`: Uのノイズに対するInvGamma事前のスケール
  * `xNoiseShape::Float64=4.0`: Xのノイズに対するInvGamma事前の形状
  * `xNoiseScale::Float64=4.0`: Xのノイズに対するInvGamma事前のスケール
  * `tNoiseShape::Float64=4.0`: Tのノイズに対するInvGamma事前の形状
  * `tNoiseScale::Float64=4.0`: Tのノイズに対するInvGamma事前のスケール
  * `yNoiseShape::Float64=4.0`: Yのノイズに対するInvGamma事前の形状
  * `yNoiseScale::Float64=4.0`: Yのノイズに対するInvGamma事前のスケール
  * `xScaleShape::Float64=4.0`: Xのカーネルスケールに対するInvGamma事前の形状
  * `xScaleScale::Float64=4.0`: Xのカーネルスケールに対するInvGamma事前のスケール
  * `tScaleShape::Float64=4.0`: Tのカーネルスケールに対するInvGamma事前の形状
  * `tScaleScale::Float64=4.0`: Tのカーネルスケールに対するInvGamma事前のスケール
  * `yScaleShape::Float64=4.0`: Yのカーネルスケールに対するInvGamma事前の形状
  * `yScaleScale::Float64=4.0`: Yのカーネルスケールに対するInvGamma事前のスケール
  * `uxLSShape::Float64=4.0`: UとXのカーネル長さスケールに対するInvGamma事前の形状
  * `uxLSScale::Float64=4.0`: UとXのカーネル長さスケールに対するInvGamma事前のスケール
  * `utLSShape::Float64=4.0`: UとTのカーネル長さスケールに対するInvGamma事前の形状
  * `utLSScale::Float64=4.0`: UとTのカーネル長さスケールに対するInvGamma事前のスケール
  * `xtLSShape::Float64=4.0`: XとTのカーネル長さスケールに対するInvGamma事前の形状
  * `xtLSScale::Float64=4.0`: XとTのカーネル長さスケールに対するInvGamma事前のスケール
  * `uyLSShape::Float64=4.0`: UとYのカーネル長さスケールに対するInvGamma事前の形状
  * `uyLSScale::Float64=4.0`: UとYのカーネル長さスケールに対するInvGamma事前のスケール
  * `xyLSShape::Float64=4.0`: XとYのカーネル長さスケールに対するInvGamma事前の形状
  * `xyLSScale::Float64=4.0`: XとYのカーネル長さスケールに対するInvGamma事前のスケール
  * `tyLSShape::Float64=4.0`: TとYのカーネル長さスケールに対するInvGamma事前の形状
  * `tyLSScale::Float64=4.0`: TとYのカーネル長さスケールに対するInvGamma事前のスケール
  * `sigmaUNoise::Float64=1.0e-13`: 共分散を安定かつ可逆にするために行列に追加されるノイズ
  * `sigmaUCov::Float64=1.0`: 構造化された交絡因子に対する仮定された共分散
  * `drift::Float64=0.5`: 論文にあるように、メトロポリス・ヘイスティングスのガウスドリフト
