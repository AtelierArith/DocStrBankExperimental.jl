```
box(t::Table, cellnumber::Int, action::Symbol=:none; vertices=false)
box(t::Table, cellnumber::Int; action=:none, vertices=false)
```

テーブル`t`のセル`cellnumber`の周りにボックスを作成します。
