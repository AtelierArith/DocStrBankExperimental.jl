```
exactlogpartitionfunction(dbm)
```

Calculates the log of the partition function of the DBM `dbm` exactly. If the number of hidden layers is even, the execution time grows exponentially with the total number of nodes in hidden layers with odd indexes (i. e. h1, h3, ...). If the number of hidden layers is odd, the execution time grows exponentially with the minimum of (number of nodes in layers with even index, number of nodes in layers with odd index).
