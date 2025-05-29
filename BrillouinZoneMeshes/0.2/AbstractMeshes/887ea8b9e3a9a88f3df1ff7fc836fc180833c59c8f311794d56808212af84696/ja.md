```
abstract type AbstractMesh{T,DIM} <: AbstractArray{SVector{T,DIM},DIM}
```

このパッケージ内のすべてのメッシュの親タイプです。

AbstractMeshのデフォルトの戻り値はSVector{T,DIM}であり、これはメッシュポイントのデカルト座標であると仮定されます。たとえメッシュ自体が極座標であってもです。極座標や分数座標などのメッシュポイントの他の表現は、traitsを使用してgetindex経由で提供される可能性があります。

# 必要なフィールド:

  * `size`: 整数のタプルとしてのメッシュのサイズ
