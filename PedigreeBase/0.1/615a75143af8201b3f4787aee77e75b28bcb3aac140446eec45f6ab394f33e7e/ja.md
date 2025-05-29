```
c = get_inbupg_code(s, d, f)
c = get_inbupg_code(pedlist, f)
```

sire ID `s`、dam ID `d`、および近親交配係数のリスト `f` から「inb/upg コード」を返します。単一のIDの代わりに、すべての個体のコードを取得するために、種雄牛と雌牛のリスト（統一リスト `pedlist` または別々のリスト `s` と `d`）を提供できます。このコードは整数であり、BLUPF90プログラムでのみ有用です。
