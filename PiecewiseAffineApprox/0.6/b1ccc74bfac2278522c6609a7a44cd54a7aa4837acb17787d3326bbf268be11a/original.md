```
Cluster
```

Compute affine approximation using the method proposed by Mangani & Boyd.

Note that this algoritm computes multiple approximations and selects the best. If julia is started with multiple threads, these are computed in parallel. Consider  how many threads will be beneficial, particularly when using a commercial solver where  the license may restrict the number of simultanous solver instances.
