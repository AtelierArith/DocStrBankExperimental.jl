```
trten2ten(B::Matrix,r1::Integer,r2::Integer)
trten2ten(B::MatrixCell,r1::Vector,r2::Vector)
```

Transfer tensor to tensor. If transfer tensor is given as a matrix, reshape it into a tensor of order 3 and size r1×r2×r3, where `r3=size(B,2)`.
