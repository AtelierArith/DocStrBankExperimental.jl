```
CovGaussianNetwork(;pre=identity, μ, Σ)
```

呼び出すと `μ` と `Σ` を返します。ここで、μ は平均、Σ は共分散行列です。GaussianNetworkとは異なり、出力は3次元です。μ の次元は `(action_size x 1 x batchsize)` で、Σ の次元は `(action_size x action_size x batchsize)` です。`CovGaussianNetwork` の Σ ヘッドは、正方行列を直接返すのではなく、長さ `action_size x (action_size + 1) ÷ 2` のベクトルを返すべきです。このベクトルには、共分散行列の上三角のコレスキー分解の要素が含まれ、そこから再構築されます。`MvNormal.(μ, Σ)` からサンプリングします。
