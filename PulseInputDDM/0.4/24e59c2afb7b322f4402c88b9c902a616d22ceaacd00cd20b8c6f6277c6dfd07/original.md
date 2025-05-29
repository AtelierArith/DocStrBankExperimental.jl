```
Hessian(model; chunck_size)
```

Compute the hessian of the negative log-likelihood at the current value of the parameters of a `neuralDDM`.

Arguments:

  * `model`: instance of `neuralDDM`

Optional arguments:

  * `chunk_size`: parameter to manange how many passes over the LL are required to compute the Hessian. Can be larger if you have access to more memory.
