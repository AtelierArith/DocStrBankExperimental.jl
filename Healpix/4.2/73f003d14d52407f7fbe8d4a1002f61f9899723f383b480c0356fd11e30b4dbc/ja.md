```
getringinfo!(resol::Resolution, ring, ringinfo::RingInfo; full=true) :: RingInfo
```

指定されたリングに関する情報でRingInfo構造体を埋めます。`full`が`false`の場合、フィールド`colatitude_rad`（計算において最も高価なもの）は`NaN`に設定されます。
