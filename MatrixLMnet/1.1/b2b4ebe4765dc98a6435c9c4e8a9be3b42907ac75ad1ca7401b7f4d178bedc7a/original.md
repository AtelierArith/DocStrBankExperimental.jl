```
resid(MLMNet::Mlmnet, lambda::Float64, alpha::Float64, newData::RawData=MLMNet.data)
```

Calculate residuals of an MLMNet object, given a lambda 

# Arguments

  * MLMNet = Mlmnet object
  * lambda = lambda penalty to use, a floating scalar
  * alpha = alpha penalty to determine the mix of penalties between L1 and L2 a floating scalar
  * newData = RawData object. Defaults to the data field in the MLM object  used to fit the model.

# Value

2d array of residuals
