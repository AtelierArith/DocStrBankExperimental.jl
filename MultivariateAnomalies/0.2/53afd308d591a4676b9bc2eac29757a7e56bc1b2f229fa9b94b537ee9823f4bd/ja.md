```
KNFST_predict!(KNFST_out, KNFST_mod, K)
```

カーネル行列 `K` で表されるデータの外れ値性を予測します。これは、`KNFST_out` オブジェクト（`init_KNFST()`）と、いくつかの KNFST モデル（`KNFST_mod = KNFST_train(K)`）およびテストカーネル行列 K を与えられた場合です。

Paul Bodesheim、Alexander Freytag、Erik Rodner、Michael Kemmler、Joachim Denzler: "Kernel Null Space Methods for Novelty Detection". Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2013.
