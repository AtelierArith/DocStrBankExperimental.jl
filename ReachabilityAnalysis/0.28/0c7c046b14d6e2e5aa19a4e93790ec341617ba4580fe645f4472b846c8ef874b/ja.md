```
A20{N} <: AbstractContinuousPost
```

不確実な入力を持つ大規模線形システムのための到達可能性メソッドの実装、Krylov部分空間からの[Althoff20](@citet)。

### フィールド

  * `δ`          – 離散化のステップサイズ
  * `max_order`  – （オプション、デフォルト: `5`）最大ゾノトープ次数

### 参考文献

[Althoff20](@citet)およびそこにある参考文献を参照してください。
