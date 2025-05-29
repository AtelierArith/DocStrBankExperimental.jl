```
ncbeta(a,b,lambda,x)
```

Compute the CDF of the noncentral beta distribution given by

$$
I_{x}(a,b; \lambda) = \sum_{j=0}^{\infty} q(\lambda/2,j) I_{x}(a+j,b;0)
$$

For $\lambda < 54$ : algorithm suggested by Lenth(1987) in `ncbeta_tail(a,b,lambda,x)`. Else for $\lambda \geq 54$: modification in Chattamvelli(1997) in `ncbeta_poisson(a,b,lambda,x)` by using both forward and backward recurrences.
