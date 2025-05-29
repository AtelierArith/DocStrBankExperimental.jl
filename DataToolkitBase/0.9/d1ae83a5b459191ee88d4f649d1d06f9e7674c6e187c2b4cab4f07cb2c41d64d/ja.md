```
UnregisteredPackage(pkg::Symbol, mod::Module)
```

パッケージ `pkg` は `mod` 内で要求されましたが、`mod` によって登録されていないため、ロードできません。

# 例の発生

```julia-repl
julia> @import Foo
ERROR: UnregisteredPackage: Foo has not been registered by Main, see @addpkg for more information
Stacktrace: [...]
```
