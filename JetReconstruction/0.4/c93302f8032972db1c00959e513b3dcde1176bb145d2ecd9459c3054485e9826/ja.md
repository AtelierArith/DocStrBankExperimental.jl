```
constituents(jet::T, cs::ClusterSequence{T}) where T <: FourMomentum
```

与えられたジェットの構成要素をクラスタ系列から取得します。

# 引数

  * `cs::ClusterSequence{T}`: クラスタ系列オブジェクト。
  * `jet::T`: 構成要素を取得するためのジェット。

# 戻り値

与えられたジェットの構成要素を表すジェットオブジェクトの配列（入力ジェットと同じ型）を返します。  
