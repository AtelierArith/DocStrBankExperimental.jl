DependencyWalkerは、Juliaで読み込まれた共有ライブラリの依存関係を辿ることができます。

このパッケージは、共有ライブラリへのパスを唯一の引数として受け取る`Library`という単一の関数をエクスポートします：

```
julia> using DependencyWalker, LibSSH2_jll

julia> LibSSH2_jll.libssh2_path # libssh2ライブラリへのパス
"/home/user/.julia/artifacts/26c7d3a6c17151277018b133ab0034e93ddc3d1e/lib/libssh2.so"

julia> Library(LibSSH2_jll.libssh2_path)
◼ /home/user/.julia/artifacts/26c7d3a6c17151277018b133ab0034e93ddc3d1e/lib/libssh2.so
  ◼ /usr/bin/../lib/julia/libmbedtls.so.12
    ◼ /usr/bin/../lib/julia/libmbedx509.so.0
...
```
