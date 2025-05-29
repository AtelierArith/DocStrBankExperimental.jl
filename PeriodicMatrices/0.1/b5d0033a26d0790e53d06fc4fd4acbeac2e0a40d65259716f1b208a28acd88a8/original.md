```
 ws_pschur(A::Array{Float64,3}) -> (QIND, SIND, ALPHAR, ALPHAI, BETA, SCAL, IWORK, DWORK)
```

Allocate workspaces for the function `pschur!` to call the SLICOT-based wrappers `mb03vw!` and `mb03bd!` avoiding additional allocations.     
