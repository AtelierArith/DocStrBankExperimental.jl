```
abstract type RotationGenerator{N,T} <: StaticMatrix{N,N,T}
```

`N`次元回転生成器を表す抽象型です。より抽象的には、彼らは歪対称実数 `N`×`N` 行列を表します。
