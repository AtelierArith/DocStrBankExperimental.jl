```
nodes(elem::AbstractElemShape,N)
```

Computes interpolation nodes of degree N. Edge nodes coincide with (N+1)-point Lobatto points. Default routine for elem = Tet(), Pyr(), Tri().

For Quad(), Hex(), Wedge() elements, nodes(...) returns interpolation points constructed using a tensor product of lower-dimensional nodes. 
