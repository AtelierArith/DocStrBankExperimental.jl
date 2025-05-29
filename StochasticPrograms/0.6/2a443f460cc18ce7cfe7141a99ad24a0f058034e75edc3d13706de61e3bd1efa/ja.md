```
has_duals(stochasticprogram::StochasticProgram; result::Int = 1)
```

`stochasticprogram`の結果インデックス`result`でソルバーが第一段階の双対解をクエリできる場合は`true`を返し、そうでない場合は`false`を返します。
