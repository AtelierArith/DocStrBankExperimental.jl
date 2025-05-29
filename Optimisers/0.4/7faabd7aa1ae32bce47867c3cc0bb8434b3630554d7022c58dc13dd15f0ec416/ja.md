```
Optimisers.freeze!(tree)
```

一時的に状態 `tree = setup(rule, model)` を変更し、パラメータが更新されないようにします。 [`thaw!`](@ref Optimisers.thaw!) によって元に戻されます。

モデルの一部に対応する状態にのみ適用でき、例えば `model::Chain` の場合、`model.layers[1]` を凍結するには `freeze!(tree.layers[1])` を呼び出す必要があります。

# 例

```jldoctest
julia> m = (x = ([1.0], 2.0), y = [3.0]);

julia> s = Optimisers.setup(Momentum(), m);

julia> Optimisers.freeze!(s.x)

julia> Optimisers.update!(s, m, (x = ([pi], 10pi), y = [100pi]));  # 偽の勾配を使用

julia> m
(x = ([1.0], 2.0), y = [-0.14159265358979312])

julia> s
(x = (Leaf(Momentum(0.01, 0.9), [0.0], frozen = true), ()), y = Leaf(Momentum(0.01, 0.9), [3.14159]))

julia> Optimisers.thaw!(s)

julia> s.x
(Leaf(Momentum(0.01, 0.9), [0.0]), ())
```
