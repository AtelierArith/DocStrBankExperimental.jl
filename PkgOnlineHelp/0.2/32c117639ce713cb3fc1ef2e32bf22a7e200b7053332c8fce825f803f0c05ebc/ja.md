```
url = pkg_site(pkgname::AbstractString; autoopen=true)
```

パッケージのホームリポジトリのURLを見つけるために、`DEPOT_PATH`内のレジストリを検索します。`autoopen`が`true`（デフォルト）であれば、デフォルトのブラウザを使用してURLを開きます。

# 例

```jldoctest
julia> pkg_site("StaticArrays")
"https://github.com/JuliaArrays/StaticArrays.jl.git"
```

この例では、ウェブサイトもユーザーのブラウザで開かれます。
