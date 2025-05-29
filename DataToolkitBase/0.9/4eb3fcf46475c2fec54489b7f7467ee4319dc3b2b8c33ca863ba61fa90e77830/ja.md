```
MissingPackage(pkg::Base.PkgId)
```

パッケージ `pkg` が要求されましたが、現在の環境では利用できないようです。

# 例の発生

```julia-repl
julia> @addpkg Bar "00000000-0000-0000-0000-000000000000"
Bar [00000000-0000-0000-0000-000000000000]

julia> @import Bar
[ Info: Lazy-loading Bar [00000000-0000-0000-0000-000000000001]
ERROR: MissingPackage: Bar [00000000-0000-0000-0000-000000000001] が要求されましたが、インストールされていないようです。
Stacktrace: [...]
```
