```
Logical{T}
```

`@variable`を使用して論理変数を作成するためのタグ。最も一般的には、次の構文を有効にするために使用されます：

```julia
@variable(model, var_expr, Logical, [kwargs...])
```

これは、最終的に次の形式のバイナリ変数に再定式化される[`LogicalVariable`](@ref)を作成します：

```julia
@variable(model, var_expr, Bin, [kwargs...])
```

再定式化された変数を作成するために使用されるタグを含めるには、構文は次のようになります：

```julia
@variable(model, var_expr, Logical(MyTag()), [kwargs...])
```

これは、`MyTag()`に関連付けられた[`LogicalVariable`](@ref)を作成し、再定式化されたバイナリ変数が次の形式になるようにします：

```julia
@variable(model, var_expr, Bin, MyTag(), [kwargs...])
```
