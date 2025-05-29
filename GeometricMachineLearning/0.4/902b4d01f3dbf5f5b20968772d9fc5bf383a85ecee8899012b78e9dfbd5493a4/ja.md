```
TransformerLoss(seq_length, prediction_window)
```

トランスフォーマー損失のインスタンスを作成します。

これは、[`TransformerIntegrator`](@ref)タイプのニューラルネットワークと一緒に使用する必要があります。

# 例

`TransformerLoss`は、入力にニューラルネットワークを適用し、$L_2$ノルムを介して`output`と比較します：

```jldoctest
using GeometricMachineLearning
using LinearAlgebra: norm
import Random

const d = 2
const seq_length = 3
const prediction_window = 2

Random.seed!(123)
arch = StandardTransformerIntegrator(d)
nn = NeuralNetwork(arch)

input_mat =  [1. 2. 3.; 4. 5. 6.]
output_mat = [1. 2.; 3. 4.]
loss = TransformerLoss(seq_length, prediction_window)

# 予測の開始
const sop = seq_length - prediction_window + 1
loss(nn, input_mat, output_mat) ≈ norm(output_mat - nn(input_mat)[:, sop:end]) / norm(output_mat)

# 出力

true
```

したがって、`TransformerLoss`は単に次のように行います：

$$
    \mathtt{loss}(\mathcal{NN}, \mathtt{input}, \mathtt{output}) = || \mathcal{NN}(\mathtt{input})[(\mathtt{sl} - \mathtt{pw} + 1):\mathtt{end}] - \mathtt{output} || / || \mathtt{output} ||,
$$

ここで、$||\cdot||$は$L_2$ノルムです。

# パラメータ

`prediction_window`は、将来の何ステップを予測するかを指定します。デフォルトでは、`seq_length`に指定された値になります。
