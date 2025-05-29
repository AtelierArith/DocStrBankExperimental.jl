```
opt_state = setup(rule, model)
```

これは `Optimisers.setup` のバージョンであり、[`train!`](@ref Flux.train!) を使用する前の最初のステップです。これは `Optimisers.setup` と異なり、以下の点があります：

  * ミュータビリティのための追加のチェックが1つあります（Fluxはモデルをインプレースで変更することを期待しているのに対し、Optimisers.jlは更新されたモデルを返すように設計されています）
  * Fluxの古いオプティマイザを受け入れ、それらを変換するメソッドがあります。（古い `Flux.Optimise.Adam` と新しい `Optimisers.Adam` は異なる型です。）

# 例

```jldoctest
julia> model = Dense(2 => 1, leakyrelu; init=ones);

julia> opt_state = Flux.setup(Momentum(0.1), model)  # これはオプティマイザとその状態をエンコードします
(weight = Leaf(Momentum(0.1, 0.9), [0.0 0.0]), bias = Leaf(Momentum(0.1, 0.9), [0.0]), σ = ())

julia> x1, y1 = [0.2, -0.3], [0.4];  # 2ステップに同じデータを使用します：

julia> Flux.train!(model, [(x1, y1), (x1, y1)], opt_state) do m, x, y
         sum(abs.(m(x) .- y)) * 100
       end

julia> model.bias  # ゼロだったが、Flux.train!によって変更された
1-element Vector{Float64}:
 10.19

julia> opt_state  # Flux.train!によって変更された
(weight = Leaf(Momentum(0.1, 0.9), [-2.018 3.027]), bias = Leaf(Momentum(0.1, 0.9), [-10.09]), σ = ())
```
