```
arrange!(X[,n::Integer])
arrange!(X[,P::Vector])
```

Arrange the rank-1 components of a ktensor: normalize the columns of the factor matrices and then sort the ktensor components by magnitude, greatest to least. Rewrite ktensor.

## Arguments:

  * `n`: Absorb the weights into the nth factor matrix instead of lambda.
  * `P`: Rearrange the components of X according to the permutation P. P should be a permutation of 1 to ncomponents(X).
