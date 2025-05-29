```
Assert(; cond, msg="")
```

条件 `cond(column)` が `false` を返す場合に `AssertionError(msg)` をスローすることで、テーブルのすべての列をアサートします。そうでない場合は、入力テーブルを返します。

`msg` 引数は文字列または列名を受け取り文字列を返す関数であることができます。例: `nm -> "error in column $nm"`。

```
Assert(col₁, col₂, ..., colₙ; cond, msg="")
Assert([col₁, col₂, ..., colₙ]; cond, msg="")
Assert((col₁, col₂, ..., colₙ); cond, msg="")
```

選択した列 `col₁`, `col₂`, ..., `colₙ` をアサートします。

```
Assert(regex; cond, msg="")
```

`regex` に一致する列をアサートします。

# 例

```julia
Assert(cond=allunique, msg="assertion error")
Assert([2, 3, 5], cond=x -> sum(x) > 100)
Assert([:b, :c, :e], cond=x -> eltype(x) <: Integer)
Assert(("b", "c", "e"), cond=allunique, msg=nm -> "error in column $nm")
Assert(r"[bce]", cond=x -> sum(x) > 100)
```
