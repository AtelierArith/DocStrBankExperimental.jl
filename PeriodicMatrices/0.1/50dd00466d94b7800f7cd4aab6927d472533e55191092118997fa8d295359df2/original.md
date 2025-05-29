```
pmaverage(A; rtol = sqrt(eps())) -> Am
```

Compute for the continuous-time periodic matrix `A(t)`  the corresponding time averaged matrix `Am` over one period.  The Gauss-Konrod quadratue method is employed for numerical integration using a relative accuracy tolerance specified by `rtol`. 
