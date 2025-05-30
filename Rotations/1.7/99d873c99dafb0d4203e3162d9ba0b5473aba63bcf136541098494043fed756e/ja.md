```
struct RotMatrixGenerator{N,T} <: RotationGenerator{N,T}
```

静的サイズのN×Nの斜め対称行列です。

注意: 入力行列の斜め対称性はコンストラクタによって*チェックされません*。
