```
iterate(nn, ics)
```

この関数は、評価目的のためにすでに訓練された [`NeuralNetworkIntegrator`](@ref) の軌道を計算します。

入力として受け取るものは次のとおりです：

1. `nn`: 訓練された `NeuralNetwork`。
2. `ics`: 初期条件（2つのベクトルの `NamedTuple`）

# 例

`iterate` を示すために、次のような単純な ResNet を使用します：

$$
\mathrm{ResNet}: x \mapsto \begin{pmatrix} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 1\end{pmatrix}x + \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
$$

そして、次のように3回繰り返します：

$$
    \mathtt{ics} = \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}.
$$

```jldoctest
using GeometricMachineLearning

model = ResNet(3, 0, identity)
weight = [1 0 0; 0 2 0; 0 0 1]
bias = [0, 0, 1]
ps = NeuralNetworkParameters((L1 = (weight = weight, bias = bias), ))
nn = NeuralNetwork(model, Chain(model), ps, CPU())

ics = [1, 1, 1]
iterate(nn, ics; n_points = 4)

# output

3×4 Matrix{Int64}:
 1  2  4   8
 1  3  9  27
 1  3  7  15
```

# 引数

オプションのキーワード引数は

  * `n_points = 100`

実行すべき積分ステップの数です。
