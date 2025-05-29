```
download_artifact(tree_hash::SHA1, tarball_url::String, tarball_hash::String;
                  verbose::Bool = false, io::IO=stderr)
```

アーティファクトをアーティファクトストアにダウンロード/インストールします。成功した場合は`true`を返し、失敗した場合はエラーオブジェクトを返します。

!!! compat "Julia 1.8"
    Julia 1.8以降、この関数は失敗が発生した場合に`false`ではなくエラーオブジェクトを返します。

