```
@apply_regionally expr
```

`expr`の関数呼び出しをローカルに分配します。

関数が何も返さない場合、[`apply_regionally!`](@ref)を呼び出します。

`expr`の関数が何かを返す場合、`@apply_regionally`は[`construct_regionally`](@ref)を呼び出します。
