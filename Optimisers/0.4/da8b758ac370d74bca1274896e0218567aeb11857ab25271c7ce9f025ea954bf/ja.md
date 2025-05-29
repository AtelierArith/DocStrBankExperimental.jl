```
Optimisers.adjust!(tree, η)
```

状態 `tree = setup(rule, model)` を変更して最適化ルールのパラメータを変更しますが、保存された状態は破壊しません。通常、トレーニングの途中で使用されます。

モデルの一部に適用することができ、状態 `tree` の対応する部分にのみ作用します。

学習率だけを変更するには、数値 `η::Real` を提供します。

# 例

```jldoctest adjust
julia> m = (vec = rand(Float32, 2), fun = sin);

julia> st = Optimisers.setup(Nesterov(), m)  # 保存されたモーメンタムはゼロに初期化されます
(vec = Leaf(Nesterov(0.001, 0.9), Float32[0.0, 0.0]), fun = ())

julia> st, m = Optimisers.update(st, m, (vec = [16, 88], fun = nothing));  # 偽の勾配で

julia> st
(vec = Leaf(Nesterov(0.001, 0.9), Float32[-0.016, -0.088]), fun = ())

julia> Optimisers.adjust!(st, 0.123)  # 学習率を変更し、保存されたモーメンタムはそのまま

julia> st
(vec = Leaf(Nesterov(0.123, 0.9), Float32[-0.016, -0.088]), fun = ())
```

他のパラメータを変更するには、`adjust!` は最適化ルールの型のフィールド名に一致するキーワード引数も受け入れます。

```jldoctest adjust
julia> fieldnames(Adam)
(:eta, :beta, :epsilon)

julia> st2 = Optimisers.setup(OptimiserChain(ClipGrad(), Adam()), m)
(vec = Leaf(OptimiserChain(ClipGrad(10.0), Adam(0.001, (0.9, 0.999), 1.0e-8)), (nothing, (Float32[0.0, 0.0], Float32[0.0, 0.0], (0.9, 0.999)))), fun = ())

julia> Optimisers.adjust(st2; beta = (0.777, 0.909), delta = 11.1)  # deltaはClipGradに作用します
(vec = Leaf(OptimiserChain(ClipGrad(11.1), Adam(0.001, (0.777, 0.909), 1.0e-8)), (nothing, (Float32[0.0, 0.0], Float32[0.0, 0.0], (0.9, 0.999)))), fun = ())

julia> Optimisers.adjust(st; beta = "no such field")  # 静かに無視されます!
(vec = Leaf(Nesterov(0.123, 0.9), Float32[-0.016, -0.088]), fun = ())
```
