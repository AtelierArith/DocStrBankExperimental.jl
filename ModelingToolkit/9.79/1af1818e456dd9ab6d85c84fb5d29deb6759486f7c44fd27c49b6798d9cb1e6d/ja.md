```julia
connect(
    var1::Union{Symbolics.Num, SymbolicUtils.BasicSymbolic, Symbolics.Arr},
    var2::Union{Symbolics.Num, SymbolicUtils.BasicSymbolic, Symbolics.Arr},
    vars::Union{Symbolics.Num, SymbolicUtils.BasicSymbolic, Symbolics.Arr}...
) -> Symbolics.Equation

```

複数の因果変数を接続します。最初の変数は出力でなければならず、すべての後続の変数は入力でなければなりません。ステートメント `connect(var1, var2, var3, ...)` は次のように展開されます：

```julia
var1 ~ var2
var1 ~ var3
# ...
```
