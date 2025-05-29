```
smuggle(stacks::Base.ExceptionStack)
```

例外スタックをスムグルします。Julia REPLでは、`err` 変数が暗黙的に定義され、最後にスローされたエラーのスタックを含みます。

# 例

```julia-repl
julia> error("foo")
ERROR: foo
Stacktrace:
[...]

julia> smuggle(err)
```
