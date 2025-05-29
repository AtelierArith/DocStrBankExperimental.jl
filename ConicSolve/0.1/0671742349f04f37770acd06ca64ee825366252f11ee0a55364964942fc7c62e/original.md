```
set_values(sdp, mask)
```

Set linear equalities of the SDP constraints where values of the SDP matrix $X$ are determined by $X_1$ and the mask.

```julia
if mask[i, j]
    X_1[i, j] = X_1[i, j]
end
```
