```
Optimisers.update(tree, model, gradient) -> (tree, model)
```

オプティマイザと勾配を使用して、モデルの学習可能なパラメータを変更します。改善されたモデルと、次の更新に必要なオプティマイザの状態を返します。初期の状態のツリーは[`setup`](@ref Optimisers.setup)から取得されます。

また、通常の`Array`や`CuArray`のモデルに対しては、より高速な[`update!`](@ref Optimisers.update!)も参照してください。

# 例

```jldoctest
julia> m = (x = Float32[1,2,3], y = tanh);

julia> t = Optimisers.setup(Descent(0.1), m)
(x = Leaf(Descent(0.1), nothing), y = ())

julia> g = (x = [1,1,1], y = nothing);  # 偽の勾配

julia> Optimisers.update(t, m, g)
((x = Leaf(Descent(0.1), nothing), y = ()), (x = Float32[0.9, 1.9, 2.9], y = tanh))
```
