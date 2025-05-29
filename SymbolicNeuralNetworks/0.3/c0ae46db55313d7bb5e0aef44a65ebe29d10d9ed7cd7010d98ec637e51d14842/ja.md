```
SymbolicPullback <: AbstractPullback
```

`SymbolicPullback`は損失関数の*シンボリックプルバック*を計算します。

# 例

```jldoctest
using SymbolicNeuralNetworks
using AbstractNeuralNetworks
using AbstractNeuralNetworks: params
import Random
Random.seed!(123)

c = Chain(Dense(2, 1, tanh))
nn = NeuralNetwork(c)
snn = SymbolicNeuralNetwork(nn)
loss = FeedForwardLoss()
pb = SymbolicPullback(snn, loss)
ps = params(nn)
typeof(pb(ps, nn.model, (rand(2), rand(1)))[2](1))

# 出力

@NamedTuple{L1::@NamedTuple{W::Matrix{Float64}, b::Vector{Float64}}}
```

# 実装

`SymbolicPullback`のインスタンスは以下を格納します。

  * `loss`: `NetworkLoss`のインスタンス、
  * `fun`: プルバックを計算するために使用される関数。

`SymbolicPullback`のインスタンスのファンクタを`model`、`ps`、`input`に呼び出すと、次のように返されます。

```julia
_pullback.loss(model, ps, input...), _pullback.fun(input..., ps)
```

ここで、2番目の出力引数は再び関数です。

# 拡張ヘルプ

以下のような一見奇妙な点に注意します。

```jldoctest
using SymbolicNeuralNetworks
using AbstractNeuralNetworks: Chain, Dense, NeuralNetwork, FeedForwardLoss, params
using Symbolics
import Random
Random.seed!(123)

c = Chain(Dense(2, 1, tanh))
nn = NeuralNetwork(c)
snn = SymbolicNeuralNetwork(nn)
loss = FeedForwardLoss()
pb = SymbolicPullback(snn, loss)
input_output = (rand(2), rand(1))
loss_and_pullback = pb(params(nn), nn.model, input_output)
# 2番目の引数を別の入力`1`に適用することに注意
pb_values = loss_and_pullback[2](1)

@variables soutput[1:SymbolicNeuralNetworks.output_dimension(nn.model)]
symbolic_pullbacks = SymbolicNeuralNetworks.symbolic_pullback(loss(nn.model, params(snn), snn.input, soutput), snn)
pb_values2 = build_nn_function(symbolic_pullbacks, params(snn), snn.input, soutput)(input_output[1], input_output[2], params(nn))

pb_values == (pb_values2 |> SymbolicNeuralNetworks._get_contents |> SymbolicNeuralNetworks._get_params)

# 出力

true
```

ここで使用した関数についての詳細は、[`symbolic_pullback`](@ref)、[`build_nn_function`](@ref)、[`_get_params`](@ref)、および[`_get_contents`](@ref)のドキュメントを参照してください。上記の式で注目すべき点は、`SymbolicPullback`のファンクタが2つのオブジェクトを返すことです。最初のオブジェクトは、関連するパラメータと入力に対して評価された損失値です。2番目のオブジェクトは、再び入力引数を受け取り、最終的に部分導関数を返す関数です。しかし、なぜこの追加のステップが必要なのでしょうか？

!!! info "逆累積"
    機械学習では、通常、[逆累積](https://en.wikipedia.org/wiki/Automatic_differentiation#Forward_and_reverse_accumulation)を行って自動微分（AD）を実行します。単純な関数の合成である関数$f = f_1\circ{}f_2\circ\cdots\circ{}f_n:\mathbb{R}^n\to\mathbb{R}^m$が与えられていると仮定すると、*逆微分*は*出力感度*から始まり、それを順次$f_n$、$f_{n-1}$などに流し込みます。したがって、次のように行います。

    $$
    (\nabla_xf)^T = (\nabla_{x}f_1)^T(\nabla_{f_1(x)}f_2)^T\cdots(\nabla_{f_{n-1}(\cdots{}x)}f_n)^T(do),
    $$

    ここで$do\in\mathbb{R}^m$は*出力感度*であり、ヤコビアンは左から順に掛け合わされます。したがって、出力から入力に向かって順次伝播します。もし$m=1、すなわち出力が1次元であれば、*出力感度*は単に$do = 1:と見なすことができます。


理論的には、この追加のステップを省略することができます：オブジェクト（`pb.fun`に格納されているもの）を返すことは、`SymbolicPullback`のインスタンスに`pb.fun(1.)`の同等物を単に格納することができるため、不必要と見なすことができます。しかし、プルバックが呼び出し可能な関数（*出力感度*に依存する）を返すことは慣習であるため、たとえ*出力感度*がスカラー量であっても、ここでも同様に行うことにしました。
