```
update_orient!(ary::AT; aryorient, sourceorientlc[, orientunit = :rad]) where {AT<:AbstractAntennaArray}
```

天線アレイ `ary` のアレイ指向を `aryorient` に、アンテナユニットの指向を `sourceorientlc` に、指向角の単位を `orientunit` に更新します。
