```
conformables{T, S, O1, O2}(map1::HealpixMap{T, O1, AA1},
                           map2::HealpixMap{S, O2, AA2}) -> Bool
conformables{T, S, O1, O2}(map1::PolarizedHealpixMap{T, O1, AA1},
                           map2::PolarizedHealpixMap{S, O2, AA2}) -> Bool
```

2つのHealpixマップが「適合可能」であるかどうかを判断します。つまり、それらの形状と順序が同じであるかどうかです。配列タイプ`AA1`と`AA2`は適合性のテストには考慮されません。
