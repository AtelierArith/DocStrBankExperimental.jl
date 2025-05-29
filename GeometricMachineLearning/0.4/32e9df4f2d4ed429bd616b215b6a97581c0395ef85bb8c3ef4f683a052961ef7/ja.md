```
AutoEncoderLoss()
```

`AutoEncoderLoss`のインスタンスを作成します。

この損失は、常に[`AutoEncoder`](@ref)タイプのニューラルネットワークと一緒に使用する必要があります（これは、そのようなネットワークをトレーニングするためのデフォルトでもあります）。

# 例

`AutoEncoderLoss`は、入力にニューラルネットワークを適用し、$L_2$ノルムを介して`output`と比較します：

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random
Random.seed!(123)

const N = 4
const n = 1
arch = SymplecticAutoencoder(2*N, 2*n)
nn = NeuralNetwork(arch)

input_vec =  [1., 2., 3., 4., 5., 6., 7., 8.]
loss = AutoEncoderLoss()

loss(nn, input_vec) ≈ norm(input_vec - nn(input_vec)) / norm(input_vec)

# output

true
```

したがって、`AutoEncoderLoss`は単に次のようにします：

$$
    \mathtt{loss}(\mathcal{NN}, \mathtt{input}) = || \mathcal{NN}(\mathtt{input}) - \mathtt{input} || / || \mathtt{input} ||,
$$

ここで、$||\cdot||$は$L_2$ノルムです。

# パラメータ

この損失にはパラメータがありません。
