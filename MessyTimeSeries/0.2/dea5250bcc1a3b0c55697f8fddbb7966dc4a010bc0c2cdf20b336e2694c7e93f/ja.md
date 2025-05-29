```
forward_backwards_rw_interpolation(X::JMatrix{Float64})
```

`X`内の各非定常系列を、時間を前後にランダムウォークの論理を用いて順番に補間します。

# 引数

  * `X`: 観測された測定値 (`nxT`)
