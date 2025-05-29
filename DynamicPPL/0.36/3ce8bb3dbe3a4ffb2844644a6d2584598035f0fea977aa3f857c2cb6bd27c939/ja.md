```
@model(expr[, warn = false])
```

確率モデルを指定するためのマクロです。

`warn`が`true`の場合、モデル定義で内部変数名が使用されていると警告が表示されます。

# 例

モデル定義:

```julia
@model function model(x, y = 42)
    ...
end
```

`Model`を生成するには、`model(xvalue)`または`model(xvalue, yvalue)`を呼び出します。
