```
mhadtv(X,Y,v,n,t='b';variant='B')
```

Mode-n matricized Hadamard product of ttensors X and Y times vector v.

  * `t='b'`:  (X ∗ Y)ₙ(X ∗ Y)ₙᵀv. Variant of multiplication (X ∗ Y)ₙ(X ∗ Y)ₙᵀ can be specified to 'A' or 'B'.
  * `t='n'`:  (X ∗ Y)ₙᵀv.
  * `t='t'`:  (X ∗ Y)ₙᵀv.

If v is a matrix, multiply column by column.
