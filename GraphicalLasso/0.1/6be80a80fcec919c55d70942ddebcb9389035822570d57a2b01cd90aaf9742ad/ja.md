```
iscov(x::AbstractMatrix{T}) where {T<:Real}
```

与えられた行列が有効な共分散行列であるかどうかをチェックします。有効な共分散行列は、正方形で対称かつ半正定値でなければなりません。

# 引数

  * `x::AbstractMatrix{T}`: チェックする入力行列。

# 戻り値

  * `Bool`: 行列が有効な共分散行列であれば `true`、そうでなければ `false`。
