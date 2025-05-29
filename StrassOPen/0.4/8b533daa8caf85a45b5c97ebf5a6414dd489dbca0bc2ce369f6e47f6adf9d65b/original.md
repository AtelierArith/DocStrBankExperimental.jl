```
C = strassen(transA, transB, alpha, A, B[,n=])
```

Perform Strassen matrix multiplication on matrices A and B giving resulant matrix C. 

#Inputs:

  * `transA`: `AbstractChar` for whether to transpose A matrix
  * `transB`: `AbstractChar` for whether to transpose B matrix
  * `alpha`: `Number` scalar multiplier
  * `A`: Input matrix
  * `B`: Input matrix
  * `n`: level of the Strassen algorithm
