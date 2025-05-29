```
IS()
```

重要度サンプリングアルゴリズム。

使用法：

```julia
IS()
```

例：

```julia
# 平均と分散が不明な単純な正規モデルを定義します。
@model function gdemo(x)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0,sqrt.(s))
    x[1] ~ Normal(m, sqrt.(s))
    x[2] ~ Normal(m, sqrt.(s))
    return s², m
end

sample(gdemo([1.5, 2]), IS(), 1000)
```
