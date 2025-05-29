```
droptol!(t::AbstractBlockTensorMap, tol=eps(real(scalartype(t)))^(3/4))
```

Remove the tensor entries of a blocktensor that have norm `≤(tol)`.
