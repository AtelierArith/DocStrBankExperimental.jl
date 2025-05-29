```
FISTA(x0,y,Hop,PARAM,mu,Nit)
```

FISTA: Solves the l2-l1 problem via Fast Iterative Shrinkage-Thresholdng Algorithm        Given a linear operator H and it's adjoint H', the algorithm minimizes        J = ||H x - y||*2^2 + mu ||x||*1, where H is the  linear operator        encapsulated in Hop

# Arguments

  * `y`:data
  * `Hop`:linear operator
  * `PARAM`:parameters to run Hop and it's adjoint
  * `mu`:trade-off parameter
  * `x0`:initial sol just to get size of x

Reference:  Beck and Teboulle,  2009, A Fast Iterative Shrinkage-Thresholding Algorithm             for Linear Inverse Problems∗ SIAM J. Imaging Science,  Vol 2 (1), 183-202
