```
LittleSet([itr]) <: AbstractSet
```

イテラブル `itr` を与えることで、少数の要素に最適化された順序付き集合を構築します。基盤となるデータは `AbstractVector` または `Tuple` として格納され、30〜50 要素に最適です。これは [`LittleDict`](@ref) に似ています。
