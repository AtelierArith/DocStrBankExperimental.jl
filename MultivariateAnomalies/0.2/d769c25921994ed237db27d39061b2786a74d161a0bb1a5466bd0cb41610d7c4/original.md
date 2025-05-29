```
KNFST_predict(model, K)
```

predict the outlierness of some data (represented by the kernel matrix `K`), given some KNFST `model` from `KNFST_train(K)`. Compute `K`with `kernel_matrix()`.

Paul Bodesheim and Alexander Freytag and Erik Rodner and Michael Kemmler and Joachim Denzler: "Kernel Null Space Methods for Novelty Detection". Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2013.
