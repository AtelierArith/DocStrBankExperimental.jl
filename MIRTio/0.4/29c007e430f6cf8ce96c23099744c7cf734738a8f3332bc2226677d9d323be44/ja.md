```
ht = read_rdb_hdr(fid::IOStream)
```

MRIスキャンのGE生データ（RDB）ヘッダーを読み取ります

ヘッダー値に`ht.key`でアクセスできるNamedTuple `ht`を返します
