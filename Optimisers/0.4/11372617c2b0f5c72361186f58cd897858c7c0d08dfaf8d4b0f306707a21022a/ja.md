```
Optimisers.setup(rule, model) -> state_tree
```

与えられた最適化手法をモデル内のすべての学習可能なパラメータに対して初期化します。関連する状態のツリーを返し、これは[`update`](@ref Optimisers.update)または[`update!`](@ref Optimisers.update!)に渡す必要があります。

# 例

```jldoctest
julia> m = (x = rand(3), y = (true, false), z = tanh);

julia> Optimisers.setup(Momentum(), m)  # mと同じフィールド名
(x = Leaf(Momentum(0.01, 0.9), [0.0, 0.0, 0.0]), y = ((), ()), z = ())
```

構造体への再帰はFunctors.jlを使用しており、パラメータを含む新しい`struct`は使用前に`Functors.@functor`でマークする必要があります。これについては[Fluxのドキュメント](https://fluxml.ai/Flux.jl/stable/models/advanced/)を参照してください。

```jldoctest
julia> struct Layer; mat; fun; end

julia> model = (lay = Layer([1 2; 3 4f0], sin), vec = [5, 6f0]);

julia> Optimisers.setup(Momentum(), model)  # 新しいstructはデフォルトで無視される
(lay = (), vec = Leaf(Momentum(0.01, 0.9), Float32[0.0, 0.0]))

julia> destructure(model)
(Float32[5.0, 6.0], Restructure(NamedTuple, ..., 2))

julia> using Functors; @functor Layer  # この型をパラメータを含むものとして注釈を付ける

julia> Optimisers.setup(Momentum(), model)
(lay = (mat = Leaf(Momentum(0.01, 0.9), Float32[0.0 0.0; 0.0 0.0]), fun = ()), vec = Leaf(Momentum(0.01, 0.9), Float32[0.0, 0.0]))

julia> destructure(model)
(Float32[1.0, 3.0, 2.0, 4.0, 5.0, 6.0], Restructure(NamedTuple, ..., 6))
```
