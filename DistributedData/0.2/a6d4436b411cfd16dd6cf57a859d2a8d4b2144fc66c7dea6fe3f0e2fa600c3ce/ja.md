```
dload(sym::Symbol, pids, files=defaultFiles(sym,pids))
```

シンボル `sym` の内容を、`pids` で指定された各ワーカーから、`files` の対応するファイル名からインポートします。
