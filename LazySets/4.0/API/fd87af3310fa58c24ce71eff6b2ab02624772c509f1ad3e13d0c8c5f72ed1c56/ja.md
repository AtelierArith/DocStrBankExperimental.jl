```
isempty(X::LazySet, witness::Bool=false)
```

集合が空であるかどうかを確認します。

### 入力

  * `X`       – 集合
  * `witness` – （オプション、デフォルト: `false`）有効化された場合は証拠を計算

### 出力

  * `witness` オプションが無効化されている場合: `true` ならば $X = ∅$
  * `witness` オプションが有効化されている場合:

      * `(true, [])` ならば $X = ∅$
      * `(false, v)` ならば $X ≠ ∅$ であるいくつかの $v ∈ X$
