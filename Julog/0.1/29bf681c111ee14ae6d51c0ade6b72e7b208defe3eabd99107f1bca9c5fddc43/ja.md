```
unify(src, dst[, occurs_check, funcs])
```

srcをdstと統一し、必要な置換の辞書を返します。

# 引数

  * `src::Term`: 統一する項。
  * `dst::Term`: 統一する項（src/dstの順序は重要ではありません）。
  * `occurs_check::Bool=true`: 発生チェックを行うかどうか。
  * `funcs::Dict=Dict()`: 評価するカスタム関数。
