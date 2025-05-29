```
constituent_indexes(jet::T, cs::ClusterSequence{T}) where T <: FourMomentum
```

与えられたジェットの構成要素である元の粒子のインデックスを返します。

# 引数

  * `jet::T`: 構成要素を取得するためのジェット。
  * `cs::ClusterSequence{T}`: クラスタシーケンスオブジェクト。

# 戻り値

与えられたジェットの元の構成要素を表すインデックスのベクター。
