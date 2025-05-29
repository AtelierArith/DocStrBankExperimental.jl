```
allows_address_type(operator, addr_or_type)
```

`operator`に対して`addr_or_type`が有効なアドレスであれば`true`を返します。それ以外の場合は`false`を返します。

[`AbstractHamiltonian`](@ref)インターフェースの一部です。

# 拡張ヘルプ

デフォルトでは`addr_or_type <: typeof(starting_address(operator))`です。オペレーターが異なるタイプのアドレスで使用できる場合は、この関数をオーバーロードしてください。
