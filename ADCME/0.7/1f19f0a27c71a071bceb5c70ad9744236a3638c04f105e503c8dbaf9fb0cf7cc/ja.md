```
BatchNormalization(dims::Int64=2; kwargs...)
```

バッチ正規化レイヤーを作成します。

# 例

```julia
b = BatchNormalization(2)
x = rand(10,2)
training = placeholder(true)
y = b(x, training)
run(sess, y)
```
