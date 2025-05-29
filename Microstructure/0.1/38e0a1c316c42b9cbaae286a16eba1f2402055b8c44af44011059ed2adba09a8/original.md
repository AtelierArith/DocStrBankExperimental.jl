```
prepare_training(arg::NetworkArg)
```

Return (`mlp`, `inputs`, `labels`, `gt`); `mlp` is the multi-layer perceptron network model for the biophysical model;  `inputs` and `labels` are arrays of signals and scaled tissue parameters used for supervised training; and `gt` is a dict containing the ground truth tissue parameters without applying scaling. Scaling is applied in the training labels to ensure different tissue parameters are roughly in the same range as they are optimized together. 
