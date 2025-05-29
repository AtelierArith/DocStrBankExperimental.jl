```
gqi_rec(dwi::MRI, mask::MRI, odf_dirs::ODF=sphere_642, σ::Float32=Float32(1.25))
```

DWIsの一般化q空間イメージング（GQI）再構成を実行し、`GQI`構造体を返します。

このメソッドを使用する場合は、次の文献を引用してください: Fang-Cheng Yeh, et al. (2010). Generalized q-sampling imaging. IEEE Transactions on Medical Imaging, 29(9), 1626–1635. https://doi.org/10.1109/TMI.2010.2045126

# 引数

  * `dwi::MRI`: 有効な`.bvec`および`.bval`フィールドを持つ`MRI`構造体に格納された一連のDWI
  * `mask::MRI`: `MRI`構造体に格納された脳マスクボリューム
  * `odf_dirs::ODF=sphere_642`: `ODF`構造体に格納されたODFテッセレーションの頂点と面
  * `σ::Float32=Float32(1.25)`: 拡散サンプリング長さ係数

# 出力

`GQI`構造体内:

  * `.odf`: 半球上のODF振幅
  * `.peak`: 3つのピークODF振幅の方向ベクトル
  * `.qa`: 3つのピーク方向ごとの定量的異方性

```
