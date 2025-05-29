```
dstore(sym::Symbol, pids, files=defaultFiles(sym,pids))
```

シンボル `sym` の内容を、`pids` で指定された各ワーカーに対応するファイル名 `files` にエクスポートします。
