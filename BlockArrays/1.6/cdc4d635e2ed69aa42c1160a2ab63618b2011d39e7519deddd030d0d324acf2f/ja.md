```
abstract AbstractBlockArray{T, N} <: AbstractArray{T, N}
```

ブロック配列を表す抽象型です。`AbstractBlockArray` インターフェースを実装する型は、この型からサブタイプを作成する必要があります。

** 型エイリアス **

  * `AbstractBlockMatrix{T}` -> `AbstractBlockArray{T, 2}`
  * `AbstractBlockVector{T}` -> `AbstractBlockArray{T, 1}`
  * `AbstractBlockVecOrMat{T}` -> `Union{AbstractBlockMatrix{T}, AbstractBlockVector{T}}`
