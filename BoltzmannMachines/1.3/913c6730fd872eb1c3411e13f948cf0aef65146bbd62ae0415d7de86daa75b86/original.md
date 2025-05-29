```
monitorweightsnorm!(monitor, rbm, epoch)
```

Computes the L2-norm of the weights matrix and the bias vectors of the `rbm` and stores the values in the `monitor`. These values can give a hint how much the updates are changing the parameters during learning.
