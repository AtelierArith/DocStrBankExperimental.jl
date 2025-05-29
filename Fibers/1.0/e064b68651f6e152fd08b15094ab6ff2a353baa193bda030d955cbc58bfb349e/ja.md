```
dsi_rec(dwi::MRI, mask::MRI, odf_dirs::ODF=sphere_642, σ::Float32=Float32(1.25))
```

拡散スペクトル画像（DSI）再構成を行い、`DSI`構造体を返します。

このメソッドを使用する場合は、次の文献を引用してください: Wedeen, V. J., et al. (2005). Mapping complex tissue architecture with diffusion spectrum magnetic resonance imaging. Magnetic resonance in medicine, 54(6), 1377–1386. https://doi.org/10.1002/mrm.20642

# 引数

  * `dwi::MRI`: 有効な `.bvec` および `.bval` フィールドを持つ `MRI` 構造体に格納された一連のDWI
  * `mask::MRI`: `MRI` 構造体に格納された脳マスクボリューム
  * `odf_dirs::ODF=sphere_642`: `ODF` 構造体に格納されたODFテッセレーションの頂点と面
  * `hann_width::Int=32`: ハニングウィンドウの幅（q空間ボクセル単位）

# 出力

`DSI` 構造体内:

  * `.pdf`: 半球上のPDF振幅
  * `.odf`: 半球上のODF振幅
  * `.peak`: 3つのピークODF振幅の方向ベクトル
  * `.qa`: 3つのピーク方向ごとの定量的異方性

```
