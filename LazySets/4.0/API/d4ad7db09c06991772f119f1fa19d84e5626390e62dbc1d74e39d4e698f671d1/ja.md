```
isuniversal(X::LazySet, witness::Bool=false)
```

集合がユニバーサルであるかどうかを確認します。

### 入力

  * `X`       – 集合
  * `witness` – （オプション、デフォルト: `false`）有効化された場合に証拠を計算

### 出力

  * `witness` オプションが無効化されている場合: `true` ならば $X = ℝ^n$
  * `witness` オプションが有効化されている場合:

      * `(true, [])` ならば $X = ℝ^n$
      * `(false, v)` ならば $X ≠ ℝ^n$ であり、ある $v ∉ X$ である
