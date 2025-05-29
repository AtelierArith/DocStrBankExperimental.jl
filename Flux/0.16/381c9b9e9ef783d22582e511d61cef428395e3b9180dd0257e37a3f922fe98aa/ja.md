```
Parallel(connection, layers...)
Parallel(connection; name = layer, ...)

入力配列を `layers` の各パスに渡し、その出力を `connection` で縮約するレイヤーを作成します。

ブロードキャスティングに似たルールに従います：

  * 入力 `x` で呼び出された場合、これは `connection([l(x) for l in layers]...)` と同等です。
  * 複数の `inputs` と1つのレイヤーの場合、代わりに `connection([layer(x) for x in inputs]...)` になります。
  * 複数の入力と複数のレイヤーがある場合、1つの入力が各レイヤーに渡されるため、`Parallel(+, f, g)(x, y) = f(x) + g(y)` となります。

[`Chain`](@ref) と同様に、サブレイヤーにはキーワードコンストラクタを使用して名前を付けることができます。これらはインデックスでアクセスできます：`m[1] == m[:name]` は最初のレイヤーです。

また、`Parallel` に1つの `identity` を持つ [`SkipConnection`](@ref) や、ブロードキャスティング `max` で縮約する [`Maxout`](@ref) も参照してください。

# 例

```

jldoctest julia> p = Parallel(+, abs2, sqrt);

julia> p(3, 4)  # == 3^2 + √4, 2つの関数と2つの入力 11.0

julia> p((3, 4))  # タプルは常にスプラット 11.0

julia> p(4)  # == 4^2 + √4, 1つの入力が2回使用される 18.0

julia> Parallel(hcat, inv)(1, 2, 4)  # 1つの関数と3つの入力 1×3 Matrix{Float64}:  1.0  0.5  0.25

```

Fluxレイヤーを使用した場合：

```

jldoctest julia> model = Chain(Dense(3 => 5),                      Parallel(vcat, Dense(5 => 4), Chain(Dense(5 => 7), Dense(7 => 4))),                      Dense(8 => 17));

julia> model(rand32(3)) |> size (17,)

julia> model2 = Parallel(+; α = Dense(10 => 2, tanh), β = Dense(5 => 2)) Parallel(   +,   α = Dense(10 => 2, tanh),             # 22パラメータ   β = Dense(5 => 2),                    # 12パラメータ )                   # 合計: 4つの配列、34パラメータ、344バイト。

julia> model2(rand32(10), rand32(5)) |> size (2,)

julia> model2[:α](rand32(10)) |> size (2,)

julia> model2[:β] == model2[2] true ```
