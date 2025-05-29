```
info_cachefile(pkgname::AbstractString) → cf
info_cachefile(pkgid::Base.PkgId) → cf
info_cachefile(pkgid::Base.PkgId, ji_cachefilename) → cf
```

パッケージキャッシュファイルのスナップショット `cf` を返します。`cf` を表示すると内容の概要が表示されますが、`cf` のフィールドを調べることでさらに情報を得ることができます（[`PkgCacheInfo`](@ref) を参照）。

`info_cachefile("MyPkg")` を呼び出した後、`using MyPkg` を実行することで、`info_cachefile` によってロードされたイメージを使用可能にすることができます。これにより、同じセッションで複数のパッケージの `cf` をロードして、より深い分析を行うことができます。

!!! warn
    セッションに既にロードされているパッケージに対して `info_cachefile` を実行すると、セッションが破損する可能性があります。クリーンなセッションで再起動し、他のパッケージをロードする前に `info_cachefile` を使用することをお勧めします。

