```julia
struct Lindblad <: OpenQuantumBase.AbstractInteraction
```

リンドブラッド演算子、レート $γ$ と対応する演算子 $L$ によって定義されます。

  * `γ`: リンドブラッドレート
  * `L`: リンドブラッド演算子
  * `size`: サイズ
