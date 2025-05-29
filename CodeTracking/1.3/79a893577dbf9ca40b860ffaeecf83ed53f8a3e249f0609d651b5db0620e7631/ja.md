```
info = pkgfiles(name::AbstractString)
info = pkgfiles(name::AbstractString, uuid::UUID)
```

指定された `name` と `uuid` によって定義されたパッケージに関する情報を持つ [`CodeTracking.PkgFiles`](@ref) 構造体を返します。このパッケージがロードされていない場合は `nothing` を返します。
