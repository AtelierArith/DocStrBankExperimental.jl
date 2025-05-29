```
FeedForwardLoss()
```

フィードフォワードニューラルネットワークの損失のインスタンスを作成します。

これは、[`NeuralNetworkIntegrator`](@ref)タイプのニューラルネットワークと一緒に使用する必要があります。

# 例

`FeedForwardLoss`は、入力に対してニューラルネットワークを適用し、$L_2$ノルムを介して`output`と比較します：

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random
Random.seed!(123)

const d = 2
arch = GSympNet(d)
nn = NeuralNetwork(arch)

input_vec =  [1., 2.]
output_vec = [3., 4.]
loss = FeedForwardLoss()

loss(nn, input_vec, output_vec) ≈ norm(output_vec - nn(input_vec)) / norm(output_vec)

# output

true
```

したがって、`FeedForwardLoss`は単に次のようにします：

$$
    \mathtt{loss}(\mathcal{NN}, \mathtt{input}, \mathtt{output}) = || \mathcal{NN}(\mathtt{input}) - \mathtt{output} || / || \mathtt{output}||,
$$

ここで、$||\cdot||$は$L_2$ノルムです。

# パラメータ

この損失にはパラメータはありません。
