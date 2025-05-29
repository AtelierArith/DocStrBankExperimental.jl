```
Optimisers.update!(tree, model, gradient) -> (tree, model)
```

オプティマイザと勾配を使用して、モデル内の学習可能なパラメータを変更します。改善されたモデルと、次の更新に必要なオプティマイザの状態を返します。初期の状態ツリーは[`setup`](@ref Optimisers.setup)から取得されます。

これは[`update`](@ref Optimisers.update)と全く同じ方法で使用されますが、古いモデル（および古い状態）内の配列を変更する可能性があるため、通常の`Array`や`CuArray`のモデルに対してはより高速です。ただし、古いモデルが完全に更新されることを期待せず、返されたモデルを使用するべきです。（元の状態ツリーは常に変更されます。各`Leaf`は可変です。）

# 例

```jldoctest
julia> using StaticArrays, Zygote, Optimisers

julia> m = (x = [1f0, 2f0], y = SA[4f0, 5f0]);  # 一部可変のモデル

julia> t = Optimisers.setup(Momentum(1/30, 0.9), m)  # 状態のツリー
(x = Leaf(Momentum(0.0333333, 0.9), Float32[0.0, 0.0]), y = Leaf(Momentum(0.0333333, 0.9), Float32[0.0, 0.0]))

julia> g = gradient(m -> sum(abs2.(m.x .+ m.y)), m)[1]  # 構造的勾配
(x = Float32[10.0, 14.0], y = Float32[10.0, 14.0])

julia> t2, m2 = Optimisers.update!(t, m, g);

julia> m2  # 更新またはupdate!の後、これが新しいモデル
(x = Float32[0.6666666, 1.5333333], y = Float32[3.6666667, 4.5333333])

julia> m2.x === m.x  # update!はこの配列を再利用して効率を上げている
true

julia> m  # 元のものは破棄されるべきで、変更される可能性があるが保証はない
(x = Float32[0.6666666, 1.5333333], y = Float32[4.0, 5.0])

julia> t == t2  # 元の状態ツリーは変更されることが保証されている
true
```
