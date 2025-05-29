```
ZScore
```

A transformer that scales and centers the data, using only the data that are avaiable to the model at training time.

For all variables in the SDM features (regardless of whether they are used), this transformer will store the observed mean and standard deviation. There is no correction on the sample size, because there is no reason to expect that the sample size will be the same for the training and prediction situation.
