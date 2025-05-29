```
FluxNLPModel(chain_ANN data_train=MLDatasets.MNIST.traindata(Float32), data_test=MLDatasets.MNIST.testdata(Float32); size_minibatch=100)
```

`chain_ANN`によって表されるニューラルネットワークから`FluxNLPModel`を構築します。`chain_ANN`は[Flux.jl](https://fluxml.ai/)を使用して構築されています。必要な他のデータは、トレーニングデータセット`data_train`に対するイテレータ、テストデータセット`data_test`に対するイテレータ、およびミニバッチのサイズ`size_minibatch`です。仮定として`(xtrn,ytrn) = Fluxnlp.data_train`とします。
