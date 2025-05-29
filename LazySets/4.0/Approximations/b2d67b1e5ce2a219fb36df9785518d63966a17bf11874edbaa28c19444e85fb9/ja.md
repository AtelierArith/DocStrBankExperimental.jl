```
overapproximate(Z::AbstractZonotope, ::Type{<:Zonotope}, r::Real)
```

ゾノトピック集合の次数を減少させます。

### 入力

  * `Z`        – ゾノトピック集合
  * `Zonotope` – 目標集合タイプ
  * `r`        – 希望する次数

### 出力

可能であれば、`r` 個の生成子を持つ新しいゾノトープ。

### アルゴリズム

このメソッドは、デフォルトのアルゴリズムを使用して `reduce_order` にフォールバックします。
