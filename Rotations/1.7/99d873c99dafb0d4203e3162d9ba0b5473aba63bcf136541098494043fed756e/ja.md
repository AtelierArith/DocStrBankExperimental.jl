```
struct RotMatrixGenerator{N,T} <: RotationGenerator{N,T}
```

静的サイズの N×N 斜め対称行列です。

注意: 入力行列の斜め対称性はコンストラクタによって*チェックされません*。
