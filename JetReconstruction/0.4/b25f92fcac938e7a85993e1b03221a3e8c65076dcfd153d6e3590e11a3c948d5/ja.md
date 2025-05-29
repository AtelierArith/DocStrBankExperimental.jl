```
parent_jets(jet::T, cs::ClusterSequence{T})::Tuple{Union{Nothing, T}, Union{Nothing, T}} where {T <: FourMomentum}
```

与えられたジェットの親ジェットをクラスタシーケンス内で見つけます。

# 引数

  * `jet::T`: 親ジェットを見つけるためのジェット。
  * `cs::ClusterSequence`: クラスタシーケンスオブジェクト。

# 戻り値

2つの要素からなるタプルで、各要素は親ジェットオブジェクトまたは`nothing`（ジェットに親がない場合）です。
