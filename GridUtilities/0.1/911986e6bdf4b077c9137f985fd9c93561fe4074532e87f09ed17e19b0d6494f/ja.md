```
set_last_ghost!(h::History,h_post::History)
```

履歴 `h` の最後のゴースト値を履歴 `h_post` の最初の要素で設定します。これは `h` が `RegularHistory` 型の場合にのみ有効です。
