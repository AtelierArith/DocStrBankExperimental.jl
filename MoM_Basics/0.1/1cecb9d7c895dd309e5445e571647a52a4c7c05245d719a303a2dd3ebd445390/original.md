```
update_orient!(ary::AT; aryorient, sourceorientlc[, orientunit = :rad]) where {AT<:AbstractAntennaArray}
```

通过机械旋转更新天线阵列 `ary` 的阵列指向为 `aryorient`，天线单元指向为 `sourceorientlc`，指向角单位为 `orientunit` 。
