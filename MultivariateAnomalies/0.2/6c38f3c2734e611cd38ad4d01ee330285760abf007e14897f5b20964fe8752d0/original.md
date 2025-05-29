```
KNFST_train(K)
```

train a one class novelty KNFST model on a Kernel matrix `K` according to Paul Bodesheim and Alexander Freytag and Erik Rodner and Michael Kemmler and Joachim Denzler: "Kernel Null Space Methods for Novelty Detection". Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2013.

# Output

`(proj, targetValue)` `proj` 	– projection vector for data points (project x via kx*proj, where kx is row vector containing kernel values of x and training data) `targetValue` – value of all training samples in the null space
