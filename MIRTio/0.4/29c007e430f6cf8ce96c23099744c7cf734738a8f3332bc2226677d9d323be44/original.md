```
ht = read_rdb_hdr(fid::IOStream)
```

Read GE raw (RDB) header for MRI scans

Returns NamedTuple `ht` with header values accessible by `ht.key`
