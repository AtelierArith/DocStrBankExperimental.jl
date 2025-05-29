```
overapproximate(lm::LinearMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray},
                dir::Type{<:AbstractDirections}) where {N}
```

カルテシアン積配列のテンプレート方向を持つ遅延線形マップを元のブロック構造を保持しながら分解します。

### 入力

  * `lm`                    – カルテシアン積配列の遅延線形マップ
  * `CartesianProductArray` – 対象セットタイプ
  * `dir`                   – 過大評価のためのテンプレート方向

### 出力

分解された線形マップを表す `CartesianProductArray`。
