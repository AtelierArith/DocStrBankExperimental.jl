```
fitted(MLMNet::Mlmnet, lambda::Float64, alpha::Float64)
```

Calculate fitted values of an Mlmnet object, given a lambda 

# Arguments

  * MLMNet = Mlmnet object
  * lambda = lambda penalty to use, a floating scalar
  * alpha = alpha penalty to determine the mix of penalties between L1 and L2 a floating scalar

# Value

2d array of fitted values
