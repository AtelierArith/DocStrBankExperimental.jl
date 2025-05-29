```
upcheck(; indirect_deps=false)
```

どのパッケージが最新でないかをチェックします。`Dict{String, Tuple{VersionNumber, VersionNumber}}`を返し、これらのキーと値のペアを含みます。

```
`PkgName => (installed_version, latest_version)`
```

キーワード引数`indirect_deps`が`true`の場合、間接依存関係も含まれます。
