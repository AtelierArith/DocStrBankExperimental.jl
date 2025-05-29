```
DepthwiseConvDims
```

深さ方向の畳み込みのための `ConvDims` の具体的なサブクラス。主に `C_in`、`C_mult` によって特徴付けられるため、`C_in`、`C_out` とは異なる。主にチャネル計算の違いのために DenseConvDims から分離されることが有用である。
