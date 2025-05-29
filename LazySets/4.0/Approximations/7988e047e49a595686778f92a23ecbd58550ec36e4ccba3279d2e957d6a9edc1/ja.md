```
overapproximate(lm::LinearMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray{N, S}}
               ) where {N, S<:LazySet}
```

カルテシアン積配列の遅延線形写像を元のブロック構造を保持しながら分解します。

### 入力

  * `lm`                    – カルテシアン積配列の遅延線形写像
  * `CartesianProductArray` – 対象セットタイプ

### 出力

分解された線形写像を表す `CartesianProductArray`。
