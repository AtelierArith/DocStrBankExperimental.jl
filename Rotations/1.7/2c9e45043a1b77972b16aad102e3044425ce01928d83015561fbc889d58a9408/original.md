```
abstract type Rotation{N,T} <: StaticMatrix{N,N,T}
```

An abstract type representing `N`-dimensional rotations. More abstractly, they represent unitary (orthogonal) `N`×`N` matrices.
