式を `lift(argtuple -> expression, args...)` に置き換えます。ここで、`args` はメインの式の中で `$` で始まるすべての式です。

# 例:

```julia
x = Observable(rand(100))
y = Observable(rand(100))
```

## 変更前

```julia
z = lift((x, y) -> x .+ y, x, y)
```

## 変更後

```julia
z = @lift($x .+ $y)
```

式がオブザーバブルに評価される場合は、その式の周りに括弧を使うこともできます。

```julia
nt = (x = Observable(1), y = Observable(2))
@lift($(nt.x) + $(nt.y))
```
