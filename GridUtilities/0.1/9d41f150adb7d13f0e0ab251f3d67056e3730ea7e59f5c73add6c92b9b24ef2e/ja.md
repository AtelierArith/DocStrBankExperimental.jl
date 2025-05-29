```
set_first_ghost!(h::History,h_pre::History)
```

履歴 `h` の最初のゴースト値を履歴 `h_pre` の最後の要素で設定します。これは `h` が `RegularHistory` 型の場合にのみ有効です。
