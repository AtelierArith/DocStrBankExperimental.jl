```
contract(X,Y)
contract(X,indX,Y,indY[,perm])
contract(X::TensorCell)
```

Contracted product of tensors. Contract indX modes of array X to indY modes of array Y and permute the result by vector perm. Default: indX=[ndims(X)], indY=[1].
