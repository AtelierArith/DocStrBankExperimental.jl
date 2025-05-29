```
Shell(name, spinorbitals)
```

*閉じた電子殻*の仕様のための型で、フィールドは次の通りです：

  * `.name`: 殻の構成 (`::String`)
  * `.spinorbit`: スピン軌道の配列 (`::Vector{Spinorbit}`)

型 `Shell` は関数 `castShell` を使って作成するのが最適です。
