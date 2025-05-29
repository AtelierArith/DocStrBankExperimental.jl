```
@var2string(var, strvar="")
```

`var`の文字列表現を返します。

`var`がString変数の場合、その変数の値を返します。そうでない場合、`var`の文字列表現（または提供された場合は`strvar`）を返します。

# 例

```julia
julia> @var2string(CCSD)
"CCSD"
julia> CCSD = "UCCSD";
julia> @var2string(CCSD)
"UCCSD"
```
