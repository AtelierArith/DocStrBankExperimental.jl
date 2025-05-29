```
KNFST_predict!(KNFST_out, KNFST_mod, K)
```

predict the outlierness of some data (represented by the kernel matrix `K`), given a `KNFST_out` object (`init_KNFST()`), some KNFST model (`KNFST_mod = KNFST_train(K)`) and the testing kernel matrix K.

Paul Bodesheim and Alexander Freytag and Erik Rodner and Michael Kemmler and Joachim Denzler: "Kernel Null Space Methods for Novelty Detection". Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2013.
