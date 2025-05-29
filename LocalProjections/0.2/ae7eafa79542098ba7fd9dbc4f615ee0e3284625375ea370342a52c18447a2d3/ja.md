```
coef(r::LocalProjectionResult, horz::Int, xwname::VarName; kwargs...)
```

水平方向 `horz` における変数 `xwname` の係数推定値を返します。

# キーワード

  * `yname::VarName=r.ynames[1]`: 結果変数の名前。
  * `lag::Int=0`: 変数 `xwname` のラグ; 0 は変数が同時的であることを意味します。
