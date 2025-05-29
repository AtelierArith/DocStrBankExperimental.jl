```
abstract type Rotation{N,T} <: StaticMatrix{N,N,T}
```

`N`次元の回転を表す抽象型。より抽象的には、単位（直交）`N`×`N`行列を表します。
