```
LinearMapBackward(VLs, VRs)
```

Storage structure for backward pass information of linear maps. Contains:

  * `VLs`: Vector of left environment tensors
  * `VRs`: Vector of right environment tensors

Used in automatic differentiation to accumulate gradients through transfer matrix operations.
