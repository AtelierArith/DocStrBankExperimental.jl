```
@contextvar var[::T] [= default]
```

`var`という名前のコンテキスト変数を宣言します。型制約`::T`とデフォルト値`= default`はオプションです。デフォルト値が型制約`::T`なしで指定された場合、その型`T = typeof(default)`が使用されます。

!!! warning
    適切なパッケージの外で定義されたコンテキスト変数は`Distributed`と動作しません。


# 例

トップレベルのコンテキスト変数はパッケージ内で宣言する必要があります：

```julia
module MyPackage
@contextvar cvar1
@contextvar cvar2 = 1
@contextvar cvar3::Int
end
```
