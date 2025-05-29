```
get_carbon_intensity(start_date::ZonedDateTime, end_date::ZonedDateTime)
```

`intensity` と `generation` という2つのフィールドを持つ NamedTuple を返します。両方のテーブルは `start_date` と `end_date` で定義された期間にわたるデータを含んでいます。`intensity` フィールドには地域の炭素強度の予測データのデータフレームが含まれ、`generation` フィールドには総発電量に対する地域の発電量のパーセントのデータフレームが含まれています。
