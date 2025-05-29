```julia
frac_correct(nn, dataset, num_samples)

```

指定された `dataset` の最初の `num_samples` の項目をニューラルネットワークが正しく分類する割合を返します。`num_samples` の項目が少ない場合は、利用可能なすべてのサンプルを使用します。

# 名前付き引数:

  * `nn::NeuralNet`: ニューラルネットワークのパラメータ。
  * `dataset::LabelledDataset`:
  * `num_samples::Integer`: 使用するサンプルの数。
