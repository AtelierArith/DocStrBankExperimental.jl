```
pseudoabsencemask(::Type{WithinRadius}, presences::SDMLayer{Bool}; distance::Number = 100.0, )
```

元の観察からの`distance`（キロメートル単位）内に擬似欠損が存在できる擬似欠損のマスクを生成します。内部的には、これを`DistanceToEvent`を使用しています。
