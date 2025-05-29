```
LobattoLegendreBasis([RealT = Float64,] polydeg::Integer)
```

Create a nodal Lobatto-Legendre basis for polynomials of degree `polydeg`.

For the special case `polydeg=0` the DG method reduces to a finite volume method. Therefore, this function sets the center point of the cell as single node. This exceptional case is currently only supported for TreeMesh!
