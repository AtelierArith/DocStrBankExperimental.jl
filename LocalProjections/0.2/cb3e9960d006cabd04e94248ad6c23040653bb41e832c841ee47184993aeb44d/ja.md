```
vcov(r::LocalProjectionResult, horz::Int, xwname1::VarName; kwargs...)
```

ホライズン `horz` における変数 `xwname1` の推定値の分散を返します。`xwname2` が指定されている場合は、`xwname1` と `xwname2` の間の共分散を返します。

# キーワード

  * `yname1::VarName=r.ynames[1]`: `xwname1` の結果変数の名前。
  * `lag1::Int=0`: 変数 `xwname1` のラグ；0であることは変数が同時的であることを意味します。
  * `xwname2::VarName=xwname1`: 共分散に関与する第二の変数。
  * `yname2::VarName=yname1`: `xwname1` の結果変数の名前。
  * `lag2::Int=lag1`: 変数 `xwname2` のラグ；0であることは変数が同時的であることを意味します。
