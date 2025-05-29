```
`ClassificationLayer(input_dim, output_dim, activation)`
```

`ClassificationLayer`のインスタンスを作成します。

`ClassificationLayer`は行列を入力として受け取り、分類に使用されるベクトルを返します。

これは次のように行います：

$$
    X \mapsto \sigma(\mathtt{compute\_vector}(AX)),
$$

ここで、$X$は行列であり、$\mathtt{compute\_vector}$はこの行列がどのようにベクトルに変換されるかを指定します。

$$
\mathtt{compute\_vector}
$$

はキーワード`average`で指定できます。

# 引数

`ClassificationLayer`には次のオプションのキーワード引数があります：

  * `average:Bool=false`。

このキーワード引数が`true`に設定されている場合、出力は次のように計算されます：

$$
    input \mapsto \frac{1}{N}\sum_{i=1}^N[\mathcal{NN}(input)]_{\bullet{}i}.
$$

`false`（デフォルト）に設定されている場合は、入力の最後の列が選択されます。

# 例

```jldoctest
using GeometricMachineLearning

l = ClassificationLayer(2, 2, identity; average = true)
ps = (weight = [1 0; 0 1], )

input = [1 2 3; 1 1 1]

l(input, ps)

# 出力

2×1 Matrix{Float64}:
 2.0
 1.0
```

```jldoctest
using GeometricMachineLearning

l = ClassificationLayer(2, 2, identity; average = false)
ps = (weight = [1 0; 0 1], )

input = [1 2 3; 1 1 1]

l(input, ps)

# 出力

2×1 Matrix{Int64}:
 3
 1
```
