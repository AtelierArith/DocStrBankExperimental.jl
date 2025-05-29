```
ToSimpleChainsAdaptor(input_dims, convert_to_array::Bool=false)
```

LuxモデルをSimpleChainsに変換するためのアダプタ。返されるモデルは依然としてLuxモデルであり、`AbstractLuxLayer`インターフェースを満たしますが、すべての内部計算はSimpleChainsを使用して行われます。

!!! warning
    `SimpleChains.jl`に変換する際に、訓練されたパラメータや状態を保持する方法はありません。


!!! warning
    `SimpleChains.jl`に変換する際に、初期化関数のいかなる種類も保持されません。


## 引数

  * `input_dims`: バッチ次元を除く入力次元のタプル。これらは`static`型である必要があります。SimpleChainsが期待するためです。
  * `convert_to_array`: SimpleChains.jlはデフォルトで`StrideArraysCore.StrideArray`を出力しますが、これは他のパッケージと組み合わせるのがうまくいかない場合があります。`convert_to_array`が`true`に設定されている場合、出力は通常の`Array`に変換されます。

## 例

```jldoctest
julia> import SimpleChains

julia> using Adapt, Lux, Random

julia> lux_model = Chain(Conv((5, 5), 1 => 6, relu), MaxPool((2, 2)),
           Conv((5, 5), 6 => 16, relu), MaxPool((2, 2)), FlattenLayer(3),
           Chain(Dense(256 => 128, relu), Dense(128 => 84, relu), Dense(84 => 10)));

julia> adaptor = ToSimpleChainsAdaptor((28, 28, 1));

julia> simple_chains_model = adapt(adaptor, lux_model); # または adaptor(lux_model)

julia> ps, st = Lux.setup(Random.default_rng(), simple_chains_model);

julia> x = randn(Float32, 28, 28, 1, 1);

julia> size(first(simple_chains_model(x, ps, st)))
(10, 1)
```
