```
function set_nsite!(sysenv::StateEnvs, nsite::Int)
```

環境の `nsite` を設定します。`nsite = 1` は単一サイト環境、`nsite = 2` は二サイト環境、その他はそのようになります。現在、`nsite = 0`、`1`、または `2` のみが使用されます。
