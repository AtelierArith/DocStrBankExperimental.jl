```
mutable struct TrainingStats
```

An object with the information of the training. 

# Fields

  * `retcode`: Report code of the optimization.
  * `losses`: Vector storing the value of the loss function at each iteration.
  * `niter`: Total number of iterations/epochs.
  * `θ`: Parameters of neural network after training
