```
time_coordinate(@nospecialize(ids::IDS), field::Symbol; error_if_not_time_dependent::Bool)
```

時間座標のインデックスを返します

`error_if_not_time_dependent == false` の場合、時間依存でない配列には `0` を返します
