```
SnpArray
SnpArray(bednm, m)
SnpArray(plknm)
SnpArray(undef, m, n)
```

生の .bed ファイルは、共有メモリマップされた Matrix{UInt8} として扱われます。行数 `m` は、`data` フィールドのサイズによって一意に決定されないため、別に保存されます。
