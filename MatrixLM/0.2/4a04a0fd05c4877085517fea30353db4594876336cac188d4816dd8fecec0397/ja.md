```
Predictors(X::AbstractArray{Float64,2}, Z::AbstractArray{Float64,2},
           hasXIntercept::Bool, hasZIntercept::Bool)
```

予測子（共変量）行列を格納するための型。ブール変数 hasXIntercept と hasZIntercept も格納します（指定されていない場合、デフォルトは false です）。
