```
KNFST_predict(model, K)
```

カーネル行列 `K` で表されるデータの外れ値性を予測します。これは、`KNFST_train(K)` から得られた KNFST `model` を用いて行います。`kernel_matrix()` を使って `K` を計算します。

Paul Bodesheim、Alexander Freytag、Erik Rodner、Michael Kemmler、Joachim Denzler: "Kernel Null Space Methods for Novelty Detection". Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2013.
