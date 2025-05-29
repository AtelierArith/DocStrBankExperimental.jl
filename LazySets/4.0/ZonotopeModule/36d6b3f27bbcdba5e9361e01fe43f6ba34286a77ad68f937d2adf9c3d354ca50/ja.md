```
linear_map!(Zout::Zonotope, M::AbstractMatrix, Z::Zonotope)
```

ゾノトープの具体的な線形写像を計算し、結果を `Zout` に格納します。

### 入力

  * `Zout` – ゾノトープ（出力）
  * `M`    – 行列
  * `Z`    – ゾノトープ

### 出力

インプレースで修正されたゾノトープ `Zout`。
