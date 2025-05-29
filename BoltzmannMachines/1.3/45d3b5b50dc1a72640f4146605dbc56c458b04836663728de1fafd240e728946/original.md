```
blocksinnoise(nsamples, nvariables; ...)
```

Produces an artificial data set where there are sequences of consecutive 1s in half of the binary samples. The samples are labeled whether they belong one of the `nblocks`. The samples are otherwise randomly generated with Bernoulli distributed noise. The first return value is a matrix that has `nsamples` rows and `nvariables` columns containing zeros and ones as values. The second return value is a vector of labels.

## Optional named arguments:

  * `noise`: Bernoulli distributed noise (probability for 1s)
  * `blocklen`: length of sequences of consecutive variables set to 1 in subgroups  of samples
  * `nblocks`: number of different locations for sequences, i.e. the number of  different subgroups with sequences of 1s
