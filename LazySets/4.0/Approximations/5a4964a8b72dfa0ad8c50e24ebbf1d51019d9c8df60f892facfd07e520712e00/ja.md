```
overapproximate(rm::ResetMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray}, oa) where {N}
```

カートesian積のリセットマップ（ゼロにリセットするのみ）を新しいカートesian積でオーバー近似します。

### 入力

  * `rm`                    – リセットマップ
  * `CartesianProductArray` – 対象セットタイプ
  * `oa`                    – オーバー近似オプション

### 出力

同じブロック構造を持つカートesian積。

### 注意事項

この実装は現在、ゼロへのリセットのみをサポートしています。

### アルゴリズム

`ResetMap`を`LinearMap`に変換し、対応する`overapproximate`メソッドを呼び出します。
