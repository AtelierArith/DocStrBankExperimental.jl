```
MultiScaleDeepEquilibriumNetwork(main_layers::Tuple, mapping_layers::Matrix,
    post_fuse_layer::Union{Nothing, Tuple}, solver,
    scales::NTuple{N, NTuple{L, Int64}}; kwargs...)
```

提案されたマルチスケール深層平衡ネットワーク [baimultiscale2020](@cite)。

## 引数

  * `main_layers`: ニューラルネットワークのタプル。各ニューラルネットワークは対応するスケールに適用されます。
  * `mapping_layers`: ニューラルネットワークの行列。各ニューラルネットワークは対応するスケールと対応する層に適用されます。
  * `post_fuse_layer`: メイン層の融合出力に適用されるニューラルネットワーク。
  * `solver`: 根を求める問題のためのソルバー。ODEソルバーと非線形ソルバーの両方がサポートされています。
  * `scales`: マルチスケールDEQのスケール。各スケールは整数のタプルです。タプルの長さは対応するメイン層の層の数です。

キーワード引数については [`DeepEquilibriumNetwork`](@ref) を参照してください。

## 例

```jldoctest
julia> main_layers = (
           Parallel(+, Dense(4 => 4, tanh; use_bias=false), Dense(4 => 4, tanh; use_bias=false)),
           Dense(3 => 3, tanh), Dense(2 => 2, tanh), Dense(1 => 1, tanh));

julia> mapping_layers = [NoOpLayer() Dense(4 => 3, tanh) Dense(4 => 2, tanh) Dense(4 => 1, tanh);
                         Dense(3 => 4, tanh) NoOpLayer() Dense(3 => 2, tanh) Dense(3 => 1, tanh);
                         Dense(2 => 4, tanh) Dense(2 => 3, tanh) NoOpLayer() Dense(2 => 1, tanh);
                         Dense(1 => 4, tanh) Dense(1 => 3, tanh) Dense(1 => 2, tanh) NoOpLayer()];

julia> model = MultiScaleDeepEquilibriumNetwork(
           main_layers, mapping_layers, nothing, NewtonRaphson(), ((4,), (3,), (2,), (1,)));

julia> rng = Xoshiro(0);

julia> ps, st = Lux.setup(rng, model);

julia> x = rand(rng, Float32, 4, 12);

julia> size.(first(model(x, ps, st)))
((4, 12), (3, 12), (2, 12), (1, 12))
```
