```
LiQSS_Data{O,M}
```

暗黙のケースにのみ必要なヘルパーデータ構造。フィールド変数は次のとおりです：

  * cd::Val{M} #
  * cacheA::MVector{1,Float64}
  * qaux::Vector{MVector{O,Float64}}
  * dxaux::Vector{MVector{O,Float64}}
