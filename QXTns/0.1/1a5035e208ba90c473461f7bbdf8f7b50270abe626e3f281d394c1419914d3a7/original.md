```
tensor_data(tensor::QXTensor; consider_hyperindices::Bool=false)
```

Get the data associated with the given tensor. If the consider_hyperindices flag is true then only the first of the hyper indices are retained. For example for a 5 rank tensor where the 2nd and 4th indices form a group of hyper indices, with this option set to true would return a rank 4 tensor where the 2nd index
