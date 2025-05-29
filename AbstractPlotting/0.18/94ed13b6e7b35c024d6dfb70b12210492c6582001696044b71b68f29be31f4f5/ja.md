式を `lift(argtuple -> expression, args...)` に置き換えます。ここで、`args` はメインの式の中で `$` で始まるすべての式です。

# 例:

```julia
x = Node(rand(100))
y = Node(rand(100))
```

## 前

```julia
z = lift((x, y) -> x .+ y, x, y)
```

## 後

```julia
z = @lift(:x .+ :y)
```

式がノードに評価される場合は、その式の周りに括弧を使用することもできます。

```julia
nt = (x = Node(1), y = Node(2))
@lift($(nt.x) + $(nt.y))
```
