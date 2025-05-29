```
reset_start_value_function(dref::DerivativeRef)::Nothing
```

既存の開始値関数を削除し、デフォルトに戻します。一般的に、これは `dref` が依存している無限パラメータを削除することによってトリガーされます。

**例**

```julia-repl
julia> reset_start_value_function(dref)
```
