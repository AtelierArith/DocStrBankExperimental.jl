```julia
ModelFit!(
    r,
    inilearnrate,
    trainloss,
    dataloss,
    ratioₜ,
    seed,
    maxepoch,
    ncount,
    minlearnrate,
    reducedlearnrate,
    showloss
)

```

Train data-driven physics-based propagation model.

  * `ini_lr`: initial learning rate
  * `trainloss`: loss function used in training and model update
  * `dataloss`: data loss function to calculate benchmarking validation error for early stopping
  * `ratioₜ`: data split ratio = number of training data/(number of training data + number of validation data)
  * set `seed` to `true` to seed random data selection order
  * `maxepoch`: maximum number of training epoches allowed
  * `ncount`: maximum number of tries before reducing learning rate
  * model training ends once learning rate is smaller than `minlearnrate`
  * learning rate is reduced by `reducedlearnrate` once `ncount` is reached
  * set `showloss` to true to display training and validation errors during the model training process, if the validation error is historically the best
