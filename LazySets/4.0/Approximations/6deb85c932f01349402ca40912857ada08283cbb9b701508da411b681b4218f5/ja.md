```
overapproximate(lm::LinearMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray},
                set_type::Type{<:LazySet}) where {N}
```

与えられたセットタイプを持つデカルト積配列の遅延線形マップを分解し、元のブロック構造を保持します。

### 入力

  * `lm`                    – デカルト積配列の遅延線形マップ
  * `CartesianProductArray` – 目標セットタイプ
  * `set_type`              – 過大評価のためのセットタイプ

### 出力

分解された線形マップを表す `CartesianProductArray`。
