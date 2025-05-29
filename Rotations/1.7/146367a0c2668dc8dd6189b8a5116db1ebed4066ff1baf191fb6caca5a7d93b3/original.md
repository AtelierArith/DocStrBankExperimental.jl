```
abstract type RotationGenerator{N,T} <: StaticMatrix{N,N,T}
```

An abstract type representing `N`-dimensional rotation generator. More abstractly, they represent skew-symmetric real `N`×`N` matrices.
