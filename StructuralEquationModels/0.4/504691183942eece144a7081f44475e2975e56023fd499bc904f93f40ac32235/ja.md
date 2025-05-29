定数損失項。他のパッケージとの比較可能性のために使用できます。

# コンストラクタ

```
SemConstant(;constant_loss, kwargs...)
```

# 引数

  * `constant_loss::Number`: 目的に追加する定数

# 例

```julia
    my_constant = SemConstant(constant_loss = 42.0)
```

# インターフェース

解析的な勾配とヘッセ行列が利用可能です。
