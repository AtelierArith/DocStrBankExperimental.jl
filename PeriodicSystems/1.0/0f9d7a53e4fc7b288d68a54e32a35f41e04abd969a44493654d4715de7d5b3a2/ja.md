```
psys = psparallel(psys1, psys2)
psys = psys1 + psys2
```

周期系 `psys1` と `psys2` の並列接続 `psys` を構築します。この結合は形式的には、`psys = psys1 + psys2` として彼らの伝達マップの加算に対応します。
