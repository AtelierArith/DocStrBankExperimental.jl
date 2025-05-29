```
apply(x::TS, dim::Int=1; fun::Function=sum)
```

時系列 `x` の次元 `dim` に沿って関数 `fun` を適用します。

  * `dim` が 1 の場合、`x` の各行に `fun` を適用し、結果の時系列（`TS`）オブジェクトを返します
  * `dim` が 2 の場合、`x` の各列に `fun` を適用し、結果の `Array` を返します
