```
trten2mat(B::Array)
trten2mat(B::TensorCell)
```

Transfer tensor to matrix. If transfer tensor is given as a tensor of order 3 and size `(r1,r2,r3)`, reshape it into a matrix of size `(r1r2,r3)`.
