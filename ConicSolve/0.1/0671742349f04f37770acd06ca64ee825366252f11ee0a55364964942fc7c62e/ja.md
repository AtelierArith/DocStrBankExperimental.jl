```
set_values(sdp, mask)
```

SDP制約の線形等式を設定します。ここで、SDP行列$X$の値は$X_1$とマスクによって決定されます。

```julia
if mask[i, j]
    X_1[i, j] = X_1[i, j]
end
```
